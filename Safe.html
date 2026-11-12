<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mail Report Tracker</title>
<style>
  :root {
    --bg: #ffffff; --fg: #37352f; --muted: #787774; --border: #e9e9e7;
    --hover: #f7f7f5; --primary: #2383e2; --done: #dbeddb; --done-fg: #1c3829;
    --pending: #fadec9; --pending-fg: #49290e; --tag-blue: #d3e5ef; --tag-blue-fg: #183347;
    --danger: #e03e3e; --radius: 6px;
  }
  * { box-sizing: border-box; }
  body { margin: 0; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Pretendard", "Malgun Gothic", sans-serif; color: var(--fg); background: var(--bg); font-size: 14px; }
  .app { max-width: 1200px; margin: 0 auto; padding: 32px 24px; }
  h1 { font-size: 28px; margin: 0 0 20px; display: flex; align-items: center; gap: 10px; }
  h1 .emoji { font-size: 30px; }

  /* Tabs */
  .toolbar { display: flex; align-items: center; justify-content: space-between; border-bottom: 1px solid var(--border); margin-bottom: 4px; }
  .tabs { display: flex; gap: 4px; }
  .tab { padding: 8px 10px; border: none; background: none; cursor: pointer; font-size: 14px; color: var(--muted); border-bottom: 2px solid transparent; margin-bottom: -1px; display: flex; gap: 6px; align-items: center; }
  .tab:hover { background: var(--hover); border-radius: var(--radius) var(--radius) 0 0; }
  .tab.active { color: var(--fg); border-bottom-color: var(--fg); font-weight: 600; }
  .tab .count { background: var(--border); border-radius: 10px; padding: 0 7px; font-size: 12px; color: var(--muted); }
  .actions { display: flex; gap: 6px; align-items: center; }
  .btn { border: 1px solid var(--border); background: var(--bg); border-radius: var(--radius); padding: 5px 10px; cursor: pointer; font-size: 13px; color: var(--fg); }
  .btn:hover { background: var(--hover); }
  .btn.primary { background: var(--primary); color: #fff; border-color: var(--primary); }
  .btn.primary:hover { background: #1b6fc4; }
  .btn.danger { color: var(--danger); }
  .search { border: 1px solid var(--border); border-radius: var(--radius); padding: 5px 10px; font-size: 13px; width: 200px; }

  /* Table */
  table { width: 100%; border-collapse: collapse; }
  th { text-align: left; font-weight: 400; color: var(--muted); font-size: 13px; padding: 8px; border-bottom: 1px solid var(--border); white-space: nowrap; }
  th .ico { margin-right: 4px; opacity: .7; }
  td { padding: 6px 8px; border-bottom: 1px solid var(--border); vertical-align: middle; }
  tr:hover td { background: var(--hover); }
  .title-cell { cursor: pointer; display: flex; align-items: center; gap: 6px; font-weight: 500; }
  .title-cell:hover { text-decoration: underline; }
  .title-cell .doc { opacity: .6; }
  .title-cell .preview { font-weight: 400; color: var(--muted); font-size: 12px; margin-left: 6px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; max-width: 240px; }
  .tag { display: inline-block; padding: 1px 8px; border-radius: 4px; font-size: 13px; white-space: nowrap; }
  .tag.blue { background: var(--tag-blue); color: var(--tag-blue-fg); }
  .tag.pending { background: var(--pending); color: var(--pending-fg); }
  .tag.done { background: var(--done); color: var(--done-fg); }
  .date { color: var(--fg); white-space: nowrap; }
  .date.overdue { color: var(--danger); font-weight: 600; }
  .date.soon { color: #d9730d; font-weight: 600; }
  .btn-done { border: 1px solid var(--border); border-radius: 4px; background: var(--bg); padding: 2px 8px; cursor: pointer; font-size: 12px; }
  .btn-done:hover { background: var(--done); border-color: var(--done); }
  .btn-restore:hover { background: var(--pending); border-color: var(--pending); }
  .row-actions { opacity: 0; transition: opacity .15s; }
  tr:hover .row-actions { opacity: 1; }
  .icon-btn { border: none; background: none; cursor: pointer; color: var(--muted); padding: 2px 6px; border-radius: 4px; font-size: 13px; }
  .icon-btn:hover { background: var(--border); }
  .add-row { padding: 8px; color: var(--muted); cursor: pointer; display: flex; align-items: center; gap: 6px; }
  .add-row:hover { background: var(--hover); border-radius: var(--radius); }
  .empty { padding: 40px; text-align: center; color: var(--muted); }

  /* Side panel (Notion-like page) */
  .overlay { position: fixed; inset: 0; background: rgba(15,15,15,.3); display: none; z-index: 10; }
  .overlay.open { display: block; }
  .panel { position: fixed; top: 0; right: 0; height: 100%; width: min(720px, 100%); background: var(--bg); box-shadow: -4px 0 24px rgba(0,0,0,.12); transform: translateX(100%); transition: transform .2s ease; z-index: 11; display: flex; flex-direction: column; }
  .panel.open { transform: translateX(0); }
  .panel-head { display: flex; justify-content: space-between; align-items: center; padding: 10px 16px; border-bottom: 1px solid var(--border); }
  .panel-body { padding: 24px 48px 48px; overflow-y: auto; flex: 1; }
  .page-title { width: 100%; border: none; outline: none; font-size: 30px; font-weight: 700; padding: 8px 0; color: var(--fg); background: transparent; }
  .page-title::placeholder { color: #c9c8c5; }
  .props { display: grid; grid-template-columns: 140px 1fr; row-gap: 6px; column-gap: 8px; margin: 12px 0 20px; padding-bottom: 16px; border-bottom: 1px solid var(--border); }
  .props label { color: var(--muted); font-size: 13px; display: flex; align-items: center; gap: 6px; padding: 4px 0; }
  .props input, .props select { border: 1px solid transparent; border-radius: 4px; padding: 4px 6px; font-size: 14px; font-family: inherit; color: var(--fg); background: transparent; width: 100%; }
  .props input:hover, .props select:hover { background: var(--hover); }
  .props input:focus, .props select:focus { outline: none; border-color: var(--primary); background: var(--bg); }
  /* Mail-like body card */
  .mail-card { border: 1px solid var(--border); border-radius: 6px; overflow: hidden; background: var(--bg); }
  .mail-head { padding: 12px 16px; border-bottom: 1px solid var(--border); background: var(--hover); font-size: 13px; color: var(--muted); display: flex; flex-wrap: wrap; gap: 6px 18px; align-items: center; }
  .mail-head b { color: var(--fg); font-weight: 600; }
  .editor-tools { display: flex; gap: 6px; align-items: center; padding: 6px 10px; border-bottom: 1px solid var(--border); font-size: 12px; color: var(--muted); }
  .editor-tools .btn { padding: 3px 8px; font-size: 12px; }
  .editor-tools .spacer { flex: 1; }
  .body-editor { width: 100%; min-height: 360px; outline: none; font-size: 15px; line-height: 1.7; font-family: inherit; color: var(--fg); background: var(--bg); padding: 16px 20px 40px; white-space: pre-wrap; word-break: break-word; overflow-wrap: anywhere; }
  .body-editor:empty::before { content: attr(data-placeholder); color: #c9c8c5; pointer-events: none; }
  .body-editor.dragover { outline: 2px dashed var(--primary); outline-offset: -6px; background: #f2f7ff; }
  .body-editor img { max-width: 100%; height: auto; display: block; margin: 8px 0; border: 1px solid var(--border); border-radius: 4px; cursor: zoom-in; }
  .body-editor img:hover { box-shadow: 0 0 0 2px var(--primary); }
  .body-editor p, .body-editor div { margin: 0; }
  .body-editor table { border-collapse: collapse; max-width: 100%; }
  .body-editor table td, .body-editor table th { border: 1px solid var(--border); padding: 2px 6px; }
  .body-editor blockquote { border-left: 3px solid var(--border); margin: 6px 0; padding-left: 10px; color: var(--muted); }
  .body-editor a { color: var(--primary); }
  .img-badge { font-size: 11px; color: var(--muted); margin-left: 6px; }
  /* Lightbox */
  .lightbox { position: fixed; inset: 0; background: rgba(0,0,0,.82); display: none; align-items: center; justify-content: center; z-index: 50; cursor: zoom-out; }
  .lightbox.open { display: flex; }
  .lightbox img { max-width: 95vw; max-height: 95vh; box-shadow: 0 8px 40px rgba(0,0,0,.5); background: #fff; }
  .save-state { font-size: 12px; color: var(--muted); }
  .hidden-file { display: none; }
  @media (max-width: 720px) { .panel-body { padding: 16px; } .hide-m { display: none; } }
</style>
</head>
<body>
<div class="app">
  <h1><span class="emoji">📬</span> Mail Report Tracker</h1>

  <div class="toolbar">
    <div class="tabs">
      <button class="tab active" data-tab="progress">▶ 진행 Report <span class="count" id="cnt-progress">0</span></button>
      <button class="tab" data-tab="done">✔ 완료 Report <span class="count" id="cnt-done">0</span></button>
    </div>
    <div class="actions">
      <input class="search" id="search" type="search" placeholder="검색 (제목/요청자/본문)">
      <button class="btn" id="btn-export" title="JSON 파일로 백업">내보내기</button>
      <button class="btn" id="btn-import" title="JSON 파일 불러오기">가져오기</button>
      <input type="file" id="file-import" class="hidden-file" accept="application/json">
      <button class="btn primary" id="btn-new">＋ 새 페이지</button>
    </div>
  </div>

  <table>
    <thead>
      <tr>
        <th style="width:70px"><span class="ico">⚑</span>완료</th>
        <th><span class="ico">Aa</span>메일 제목</th>
        <th style="width:110px"><span class="ico">📅</span>접수일</th>
        <th style="width:110px"><span class="ico">📅</span>회신 요청일</th>
        <th style="width:110px"><span class="ico">◎</span>요청자</th>
        <th style="width:100px" class="hide-m"><span class="ico">◎</span>상태</th>
        <th style="width:40px"></th>
      </tr>
    </thead>
    <tbody id="tbody"></tbody>
  </table>
  <div class="add-row" id="add-row">＋ 새 페이지</div>
</div>

<!-- Notion-like detail panel -->
<div class="overlay" id="overlay"></div>
<aside class="panel" id="panel">
  <div class="panel-head">
    <div style="display:flex;gap:6px;align-items:center">
      <button class="icon-btn" id="btn-close" title="닫기 (Esc)">» 닫기</button>
      <span class="save-state" id="save-state"></span>
    </div>
    <div style="display:flex;gap:6px">
      <button class="btn" id="btn-toggle-status"></button>
      <button class="btn danger" id="btn-delete">삭제</button>
    </div>
  </div>
  <div class="panel-body">
    <input class="page-title" id="f-title" placeholder="메일 제목을 입력하세요">
    <div class="props">
      <label>📅 접수일</label>      <input type="date" id="f-received">
      <label>📅 회신 요청일</label>  <input type="date" id="f-due">
      <label>◎ 요청자</label>       <input type="text" id="f-requester" placeholder="요청자 이름">
      <label>◎ 상태</label>
      <select id="f-status">
        <option value="progress">진행</option>
        <option value="done">완료</option>
      </select>
    </div>
    <div class="mail-card">
      <div class="mail-head" id="mail-head"></div>
      <div class="editor-tools">
        <button class="btn" id="btn-attach-img" title="이미지 파일 삽입">🖼 이미지 삽입</button>
        <input type="file" id="file-img" class="hidden-file" accept="image/*" multiple>
        <span>Ctrl+V 로 캡처 이미지·메일 본문을 그대로 붙여넣을 수 있습니다. (이미지는 드래그&드롭도 가능)</span>
        <span class="spacer"></span>
        <span id="body-size"></span>
      </div>
      <div class="body-editor" id="f-body" contenteditable="true" spellcheck="false"
           data-placeholder="본문을 입력하거나 메일 내용을 붙여넣으세요… (이미지 포함, 자동 저장됩니다)"></div>
    </div>
  </div>
</aside>
<div class="lightbox" id="lightbox"><img id="lightbox-img" alt=""></div>

<script>
(function () {
  const STORAGE_KEY = 'mail-report-tracker-v1';
  const $ = (s) => document.querySelector(s);

  // ---------- State ----------
  let items = load();
  let currentTab = 'progress';
  let currentId = null;
  let saveTimer = null;

  function load() {
    try {
      const raw = localStorage.getItem(STORAGE_KEY);
      if (raw) return migrate(JSON.parse(raw));
    } catch (e) { console.warn(e); }
    // 초기 샘플 데이터 (최초 1회)
    return [
      { id: uid(), title: 'CHEMICAL 발주 규격 개정 관련 논의 내용 공유 및 확인 요청', received: '2026-11-12', due: '2026-11-27', requester: '서영호', status: 'progress', body: '', bodyIsHtml: true, updatedAt: Date.now() },
      { id: uid(), title: '외함 LPC 투자 관련하여 Program 부분 확인 요청', received: '2026-11-07', due: '2026-11-13', requester: '서영호', status: 'progress', body: '<div>• 전장팀 진행하고 있었음</div>', bodyIsHtml: true, updatedAt: Date.now() },
      { id: uid(), title: '3TANK M&S 설비 설계 간 검토 부탁 드립니다.', received: '2026-11-07', due: '2026-11-20', requester: '서영호', status: 'progress', body: '', bodyIsHtml: true, updatedAt: Date.now() },
      { id: uid(), title: 'CCSS 공급설비 표준화 도면 공유 및 검토 부탁 드립니다.', received: '2026-10-29', due: '2026-11-10', requester: '서영호', status: 'progress', body: '', bodyIsHtml: true, updatedAt: Date.now() },
      { id: uid(), title: 'TRS POU A/V Solenoid 분리 관련 조사', received: '2026-10-29', due: '', requester: '임동궁', status: 'done', body: '', bodyIsHtml: true, updatedAt: Date.now() }
    ];
  }
  function persist() {
    try {
      localStorage.setItem(STORAGE_KEY, JSON.stringify(items));
      setSaveState('저장됨');
    } catch (e) {
      console.error(e);
      setSaveState('⚠ 저장 실패 (용량 초과)');
      alert('브라우저 저장 용량(약 5MB)을 초과했습니다.\n이미지가 많은 오래된 Report를 삭제하거나, 내보내기로 백업 후 정리해 주세요.');
    }
  }
  // 기존(텍스트) 본문 → HTML 로 1회 변환
  function migrate(list) {
    return list.map(i => {
      if (!i.bodyIsHtml) { i.body = i.body ? esc(i.body).replace(/\n/g, '<br>') : ''; i.bodyIsHtml = true; }
      return i;
    });
  }
  // HTML → 검색/미리보기용 평문
  function plain(html) {
    const d = document.createElement('div'); d.innerHTML = html || '';
    d.querySelectorAll('br, p, div, li, tr').forEach(el => el.insertAdjacentText('afterend', '\n'));
    return d.textContent.replace(/\n{2,}/g, '\n').trim();
  }
  function imgCount(html) { return (html || '').match(/<img\b/gi)?.length || 0; }
  // 붙여넣은 HTML 정화 (스크립트·이벤트 제거, 이미지·표·서식은 유지)
  const BLOCK_TAGS = new Set(['SCRIPT', 'STYLE', 'IFRAME', 'OBJECT', 'EMBED', 'LINK', 'META', 'FORM', 'INPUT', 'BUTTON', 'TEXTAREA', 'SELECT', 'HEAD', 'TITLE', 'NOSCRIPT']);
  function sanitize(html) {
    const doc = new DOMParser().parseFromString('<body>' + (html || '') + '</body>', 'text/html');
    const walk = (node) => {
      [...node.children].forEach(el => {
        if (BLOCK_TAGS.has(el.tagName)) { el.remove(); return; }
        [...el.attributes].forEach(a => {
          const n = a.name.toLowerCase(), v = a.value.trim();
          if (n.startsWith('on') || n === 'id' || n === 'class' || n === 'contenteditable') el.removeAttribute(a.name);
          else if ((n === 'href' || n === 'src') && /^\s*(javascript|vbscript):/i.test(v)) el.removeAttribute(a.name);
        });
        if (el.tagName === 'IMG') {
          const s = el.getAttribute('src') || '';
          if (!/^(data:image\/|https?:|blob:)/i.test(s)) { // cid:, file: 등 로드 불가 이미지
            const ph = doc.createElement('span'); ph.textContent = '[이미지: 캡처 후 Ctrl+V 로 다시 붙여넣어 주세요]'; ph.style.color = '#b45309';
            el.replaceWith(ph); return;
          }
          el.removeAttribute('width'); el.removeAttribute('height');
          el.style.maxWidth = '100%'; el.style.height = 'auto';
        }
        if (el.tagName === 'A') { el.setAttribute('target', '_blank'); el.setAttribute('rel', 'noopener'); }
        walk(el);
      });
    };
    walk(doc.body);
    return doc.body.innerHTML;
  }
  // 이미지 파일 → (필요시 축소된) dataURL
  function fileToDataURL(file, maxW = 1600, quality = 0.85) {
    return new Promise((resolve, reject) => {
      const r = new FileReader();
      r.onload = () => {
        const img = new Image();
        img.onload = () => {
          const scale = Math.min(1, maxW / img.width);
          if (scale === 1 && file.size < 400 * 1024) return resolve(r.result);
          const c = document.createElement('canvas');
          c.width = Math.round(img.width * scale); c.height = Math.round(img.height * scale);
          const ctx = c.getContext('2d'); ctx.fillStyle = '#fff'; ctx.fillRect(0, 0, c.width, c.height); ctx.drawImage(img, 0, 0, c.width, c.height);
          resolve(c.toDataURL('image/jpeg', quality));
        };
        img.onerror = reject; img.src = r.result;
      };
      r.onerror = reject; r.readAsDataURL(file);
    });
  }
  function insertAtCaret(node) {
    const ed = $('#f-body'); ed.focus();
    const sel = window.getSelection();
    if (!sel.rangeCount || !ed.contains(sel.anchorNode)) { ed.appendChild(node); }
    else { const rg = sel.getRangeAt(0); rg.deleteContents(); rg.insertNode(node); rg.setStartAfter(node); rg.collapse(true); sel.removeAllRanges(); sel.addRange(rg); }
    ed.dispatchEvent(new Event('input', { bubbles: true }));
  }
  function insertHtml(html) {
    const frag = document.createRange().createContextualFragment(html);
    const last = frag.lastChild;
    const ed = $('#f-body'); ed.focus();
    const sel = window.getSelection();
    if (!sel.rangeCount || !ed.contains(sel.anchorNode)) ed.appendChild(frag);
    else { const rg = sel.getRangeAt(0); rg.deleteContents(); rg.insertNode(frag); if (last) { rg.setStartAfter(last); rg.collapse(true); sel.removeAllRanges(); sel.addRange(rg); } }
    ed.dispatchEvent(new Event('input', { bubbles: true }));
  }
  async function insertImageFiles(files) {
    for (const f of files) {
      if (!f.type.startsWith('image/')) continue;
      const url = await fileToDataURL(f);
      const img = document.createElement('img'); img.src = url; img.alt = f.name || 'image';
      insertAtCaret(img);
      insertAtCaret(document.createElement('br'));
    }
  }
  function updateBodySize() {
    const kb = Math.round(($('#f-body').innerHTML.length * 2) / 1024);
    $('#body-size').textContent = kb ? `본문 ${kb >= 1024 ? (kb / 1024).toFixed(1) + ' MB' : kb + ' KB'}` : '';
  }
  function renderMailHead(it) {
    const parts = [];
    if (it.requester) parts.push(`보낸사람 <b>${esc(it.requester)}</b>`);
    if (it.received) parts.push(`접수 <b>${fmt(it.received)}</b>`);
    if (it.due) parts.push(`회신 요청 <b>${fmt(it.due)}</b>`);
    $('#mail-head').innerHTML = parts.join('<span style="color:var(--border)">|</span>') || '<span>요청자·날짜를 입력하면 여기에 표시됩니다</span>';
  }
  function uid() { return Date.now().toString(36) + Math.random().toString(36).slice(2, 7); }
  function today() { return new Date().toISOString().slice(0, 10); }
  function esc(s) { return String(s ?? '').replace(/[&<>"']/g, c => ({ '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#39;' }[c])); }
  function fmt(d) { return d ? d.replaceAll('-', '/') : ''; }
  function setSaveState(t) { $('#save-state').textContent = t; }

  // ---------- Render ----------
  function render() {
    const q = $('#search').value.trim().toLowerCase();
    const list = items
      .filter(i => i.status === currentTab)
      .filter(i => !q || [i.title, i.requester, plain(i.body)].join(' ').toLowerCase().includes(q))
      .sort((a, b) => (b.received || '').localeCompare(a.received || '') || b.updatedAt - a.updatedAt);

    $('#cnt-progress').textContent = items.filter(i => i.status === 'progress').length;
    $('#cnt-done').textContent = items.filter(i => i.status === 'done').length;

    const tbody = $('#tbody');
    if (!list.length) {
      tbody.innerHTML = `<tr><td colspan="7" class="empty">${currentTab === 'progress' ? '진행 중인 Report가 없습니다.' : '완료된 Report가 없습니다.'}</td></tr>`;
      return;
    }
    const t = today();
    tbody.innerHTML = list.map(i => {
      let dueCls = 'date';
      if (i.status === 'progress' && i.due) {
        if (i.due < t) dueCls += ' overdue';
        else if (daysBetween(t, i.due) <= 3) dueCls += ' soon';
      }
      const preview = plain(i.body).split('\n')[0] || '';
      const nImg = imgCount(i.body);
      return `
      <tr data-id="${i.id}">
        <td>${i.status === 'progress'
          ? `<button class="btn-done" data-act="done" title="완료 처리 (목록에서 숨김)">완료</button>`
          : `<button class="btn-done btn-restore" data-act="restore" title="진행으로 복원">복원</button>`}</td>
        <td><div class="title-cell" data-act="open"><span class="doc">📄</span><span>${esc(i.title) || '<span style="color:#c9c8c5">제목 없음</span>'}</span>${preview ? `<span class="preview">${esc(preview)}</span>` : ''}${nImg ? `<span class="img-badge">🖼 ${nImg}</span>` : ''}</div></td>
        <td class="date">${fmt(i.received)}</td>
        <td class="${dueCls}">${fmt(i.due)}</td>
        <td>${i.requester ? `<span class="tag blue">${esc(i.requester)}</span>` : ''}</td>
        <td class="hide-m">${i.status === 'done' ? '<span class="tag done">완료</span>' : '<span class="tag pending">보관 진행</span>'}</td>
        <td><span class="row-actions"><button class="icon-btn" data-act="delete" title="삭제">🗑</button></span></td>
      </tr>`;
    }).join('');
  }
  function daysBetween(a, b) { return Math.round((new Date(b) - new Date(a)) / 86400000); }

  // ---------- Panel ----------
  function openPanel(id) {
    const it = items.find(i => i.id === id);
    if (!it) return;
    currentId = id;
    $('#f-title').value = it.title || '';
    $('#f-received').value = it.received || '';
    $('#f-due').value = it.due || '';
    $('#f-requester').value = it.requester || '';
    $('#f-status').value = it.status;
    $('#f-body').innerHTML = sanitize(it.body || '');
    renderMailHead(it); updateBodySize();
    updateToggleBtn(it);
    setSaveState('');
    $('#overlay').classList.add('open');
    $('#panel').classList.add('open');
    if (!it.title) $('#f-title').focus(); else $('#f-body').focus();
  }
  function closePanel() {
    flushSave();
    $('#overlay').classList.remove('open');
    $('#panel').classList.remove('open');
    currentId = null;
    render();
  }
  function updateToggleBtn(it) {
    $('#btn-toggle-status').textContent = it.status === 'progress' ? '✔ 완료 처리' : '↩ 진행으로 복원';
  }
  function scheduleSave() {
    setSaveState('저장 중…');
    clearTimeout(saveTimer);
    saveTimer = setTimeout(flushSave, 300);
  }
  function flushSave() {
    clearTimeout(saveTimer);
    if (!currentId) return;
    const it = items.find(i => i.id === currentId);
    if (!it) return;
    it.title = $('#f-title').value.trim();
    it.received = $('#f-received').value;
    it.due = $('#f-due').value;
    it.requester = $('#f-requester').value.trim();
    it.status = $('#f-status').value;
    it.body = sanitize($('#f-body').innerHTML); it.bodyIsHtml = true;
    renderMailHead(it); updateBodySize();
    it.updatedAt = Date.now();
    updateToggleBtn(it);
    persist();
  }

  // ---------- Actions ----------
  function createNew() {
    const it = { id: uid(), title: '', received: today(), due: '', requester: '', status: 'progress', body: '', bodyIsHtml: true, updatedAt: Date.now() };
    items.unshift(it);
    persist();
    switchTab('progress');
    openPanel(it.id);
  }
  function setStatus(id, status) {
    const it = items.find(i => i.id === id);
    if (!it) return;
    it.status = status; it.updatedAt = Date.now();
    persist(); render();
  }
  function remove(id) {
    const it = items.find(i => i.id === id);
    if (!it) return;
    if (!confirm(`"${it.title || '제목 없음'}" 을(를) 삭제할까요?`)) return;
    items = items.filter(i => i.id !== id);
    persist();
    if (currentId === id) { currentId = null; $('#overlay').classList.remove('open'); $('#panel').classList.remove('open'); }
    render();
  }
  function switchTab(tab) {
    currentTab = tab;
    document.querySelectorAll('.tab').forEach(b => b.classList.toggle('active', b.dataset.tab === tab));
    render();
  }
  function exportJson() {
    const blob = new Blob([JSON.stringify(items, null, 2)], { type: 'application/json' });
    const a = document.createElement('a');
    a.href = URL.createObjectURL(blob);
    a.download = `mail-report-${today()}.json`;
    a.click();
    URL.revokeObjectURL(a.href);
  }
  function importJson(file) {
    const r = new FileReader();
    r.onload = () => {
      try {
        const data = JSON.parse(r.result);
        if (!Array.isArray(data)) throw new Error('형식 오류');
        const mode = confirm('기존 데이터에 병합할까요?\n(취소 = 기존 데이터를 덮어쓰기)');
        if (mode) {
          const map = new Map(items.map(i => [i.id, i]));
          data.forEach(d => { const o = map.get(d.id); if (!o || (d.updatedAt || 0) > (o.updatedAt || 0)) map.set(d.id, d); });
          items = [...map.values()];
        } else items = data;
        persist(); render();
      } catch (e) { alert('JSON 파일을 읽을 수 없습니다: ' + e.message); }
    };
    r.readAsText(file);
  }

  // ---------- Events ----------
  document.querySelectorAll('.tab').forEach(b => b.addEventListener('click', () => switchTab(b.dataset.tab)));
  $('#search').addEventListener('input', render);
  $('#btn-new').addEventListener('click', createNew);
  $('#add-row').addEventListener('click', createNew);
  $('#btn-export').addEventListener('click', exportJson);
  $('#btn-import').addEventListener('click', () => $('#file-import').click());
  $('#file-import').addEventListener('change', e => { if (e.target.files[0]) importJson(e.target.files[0]); e.target.value = ''; });

  $('#tbody').addEventListener('click', e => {
    const el = e.target.closest('[data-act]');
    if (!el) return;
    const id = e.target.closest('tr').dataset.id;
    const act = el.dataset.act;
    if (act === 'open') openPanel(id);
    else if (act === 'done') setStatus(id, 'done');
    else if (act === 'restore') setStatus(id, 'progress');
    else if (act === 'delete') remove(id);
  });

  $('#overlay').addEventListener('click', closePanel);
  $('#btn-close').addEventListener('click', closePanel);
  $('#btn-delete').addEventListener('click', () => currentId && remove(currentId));
  $('#btn-toggle-status').addEventListener('click', () => {
    const sel = $('#f-status');
    sel.value = sel.value === 'progress' ? 'done' : 'progress';
    flushSave();
  });
  ['#f-title', '#f-received', '#f-due', '#f-requester', '#f-status', '#f-body'].forEach(s => {
    $(s).addEventListener('input', scheduleSave);
    $(s).addEventListener('change', scheduleSave);
  });
  // ---- 본문 에디터: 이미지/HTML 붙여넣기, 드래그&드롭, 이미지 확대 ----
  const editor = $('#f-body');
  editor.addEventListener('paste', async e => {
    const cd = e.clipboardData; if (!cd) return;
    const imgFiles = [...cd.items].filter(it => it.kind === 'file' && it.type.startsWith('image/')).map(it => it.getAsFile()).filter(Boolean);
    const html = cd.getData('text/html');
    const text = cd.getData('text/plain');
    e.preventDefault();
    if (imgFiles.length) {
      const hasText = (text || '').trim().length > 0;
      if (html && hasText) {
        // 메일 본문(텍스트+이미지) 함께 복사된 경우: 로드 불가(cid:) 이미지를 클립보드 이미지로 대체
        const doc = new DOMParser().parseFromString(html, 'text/html');
        const broken = [...doc.querySelectorAll('img')].filter(im => !/^(data:image\/|https?:|blob:)/i.test(im.getAttribute('src') || ''));
        for (let k = 0; k < broken.length && k < imgFiles.length; k++) broken[k].src = await fileToDataURL(imgFiles[k]);
        insertHtml(sanitize(doc.body.innerHTML));
        if (imgFiles.length > broken.length) await insertImageFiles(imgFiles.slice(broken.length));
        return;
      }
      await insertImageFiles(imgFiles);   // 캡처 이미지 / 이미지 파일 붙여넣기
      return;
    }
    if (html) { insertHtml(sanitize(html)); return; }   // 메일 본문 등 서식 포함 붙여넣기
    if (text) insertHtml(esc(text).replace(/\r?\n/g, '<br>'));
  });
  editor.addEventListener('dragover', e => { e.preventDefault(); editor.classList.add('dragover'); });
  editor.addEventListener('dragleave', () => editor.classList.remove('dragover'));
  editor.addEventListener('drop', async e => {
    e.preventDefault(); editor.classList.remove('dragover');
    const files = [...(e.dataTransfer?.files || [])].filter(f => f.type.startsWith('image/'));
    if (files.length) await insertImageFiles(files);
  });
  editor.addEventListener('click', e => {
    if (e.target.tagName === 'IMG') { $('#lightbox-img').src = e.target.src; $('#lightbox').classList.add('open'); }
  });
  editor.addEventListener('input', updateBodySize);
  $('#lightbox').addEventListener('click', () => $('#lightbox').classList.remove('open'));
  $('#btn-attach-img').addEventListener('click', () => $('#file-img').click());
  $('#file-img').addEventListener('change', async e => { await insertImageFiles([...e.target.files]); e.target.value = ''; });
  ['#f-received', '#f-due', '#f-requester'].forEach(s => $(s).addEventListener('input', () => {
    const it = items.find(i => i.id === currentId); if (!it) return;
    renderMailHead({ requester: $('#f-requester').value, received: $('#f-received').value, due: $('#f-due').value });
  }));

  document.addEventListener('keydown', e => {
    if (e.key === 'Escape' && $('#lightbox').classList.contains('open')) { $('#lightbox').classList.remove('open'); return; }
    if (e.key === 'Escape' && currentId) closePanel();
    if ((e.ctrlKey || e.metaKey) && e.key.toLowerCase() === 'n') { e.preventDefault(); createNew(); }
  });

  render();
})();
</script>
</body>
</html>

