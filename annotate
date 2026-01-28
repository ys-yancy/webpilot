var Lt=Object.defineProperty;var Ft=(t,n,e)=>n in t?Lt(t,n,{enumerable:!0,configurable:!0,writable:!0,value:e}):t[n]=e;var E=(t,n,e)=>Ft(t,typeof n!="symbol"?n+"":n,e);(function(){const n=document.createElement("link").relList;if(n&&n.supports&&n.supports("modulepreload"))return;for(const a of document.querySelectorAll('link[rel="modulepreload"]'))o(a);new MutationObserver(a=>{for(const s of a)if(s.type==="childList")for(const r of s.addedNodes)r.tagName==="LINK"&&r.rel==="modulepreload"&&o(r)}).observe(document,{childList:!0,subtree:!0});function e(a){const s={};return a.integrity&&(s.integrity=a.integrity),a.referrerPolicy&&(s.referrerPolicy=a.referrerPolicy),a.crossOrigin==="use-credentials"?s.credentials="include":a.crossOrigin==="anonymous"?s.credentials="omit":s.credentials="same-origin",s}function o(a){if(a.ep)return;a.ep=!0;const s=e(a);fetch(a.href,s)}})();function zt(t){let n={...t};const e=new Set;let o=!1,a=!1,s=!1;const r=()=>{s||e.forEach(c=>{try{if(c.selector){const m=c.selector(n);Object.is(m,c.prevSelected)||(c.prevSelected=m,c.listener(n))}else c.listener(n)}catch(m){console.error("[Annotation Store] Listener error:",m)}})};return{getState:()=>n,setState:c=>{if(s)return;const m=typeof c=="function"?c(n):c,y={...n,...m};Object.keys(m).some(v=>!Object.is(n[v],y[v]))&&(n=y,o?a=!0:r())},subscribe:(c,m)=>{if(s)return()=>{};const y={listener:c,selector:m,prevSelected:m?m(n):void 0};return e.add(y),()=>{e.delete(y)}},batch:c=>{if(!s){o=!0,a=!1;try{c()}finally{o=!1,a&&r()}}},reset:c=>{s||(n={...c},r())},destroy:()=>{s=!0,e.clear()}}}function Pt(){const t=new Map;let n=!1;const e=(i,d)=>{if(n)return;const h=t.get(i);if(!h)return;Array.from(h).forEach(p=>{try{p(d)}catch(l){console.error(`[Annotation EventBus] Error in handler for "${String(i)}":`,l)}})},o=(i,d)=>{if(n)return()=>{};t.has(i)||t.set(i,new Set);const h=t.get(i);return h.add(d),()=>{h.delete(d),h.size===0&&t.delete(i)}};return{emit:e,on:o,once:(i,d)=>{const h=o(i,u=>{h(),d(u)});return h},off:i=>{n||(i!==void 0?t.delete(i):t.clear())},destroy:()=>{n=!0,t.clear()}}}const ht={theme:"auto",outputLevel:"standard",toolbarPosition:"bottom-right",showTooltips:!0,showMarkerNumbers:!0,freezeOnScope:!1,persistScopes:!0,scopeColor:"#AF52DE",blockInteractions:!0,autoClearAfterCopy:!1},Yt={x:20,y:20};function Rt(t){return{scopes:new Map,selectedAnnotationId:null,hoveredElement:null,hoveredElementInfo:null,mode:"disabled",toolbarExpanded:!1,toolbarPosition:{...Yt},settings:{...ht},isSelecting:!1,selectionRect:null,selectionPreviewElements:[],isFrozen:!1,popupVisible:!1,popupAnnotationId:null,popupElementInfo:null,popupClickX:0,popupClickY:0,pendingMarkerX:0,pendingMarkerY:0,pendingMarkerIsFixed:!1,multiSelectElements:[],multiSelectInfos:[],markersVisible:!0,animatingMarkers:new Set,exitingMarkers:new Set,deletingMarkerId:null,renumberFrom:null,showCopiedFeedback:!1,showClearedFeedback:!1,scrollY:0,showEntranceAnimation:!0,isDraggingToolbar:!1,settingsPanelVisible:!1,...t}}const Ht=40;function k(t,n=Ht){const e=t.trim().replace(/\s+/g," ");return e.length<=n?e:e.slice(0,n-3)+"..."}function M(t){var e;if(t instanceof HTMLInputElement||t instanceof HTMLTextAreaElement)return t.value||t.placeholder||"";if(t instanceof HTMLSelectElement)return((e=t.options[t.selectedIndex])==null?void 0:e.text)||"";const n=t.cloneNode(!0);return n.querySelectorAll('script, style, [aria-hidden="true"]').forEach(o=>o.remove()),n.textContent||""}function P(t){const n=t.getAttribute("aria-label");if(n)return n;const e=t.getAttribute("aria-labelledby");if(e){const o=document.getElementById(e);if(o)return M(o)}return null}function ot(t){var o;const n=t.id;if(n){const a=document.querySelector(`label[for="${n}"]`);if(a)return M(a)}const e=t.closest("label");if(e){const a=e.cloneNode(!0);a.querySelectorAll("input, select, textarea").forEach(r=>r.remove());const s=(o=a.textContent)==null?void 0:o.trim();if(s)return s}return null}function mt(t){const n=Array.from(t.children);if(n.length===0)return!1;const e=n.every(a=>a.tagName==="SVG"||a.tagName==="svg"||a.classList.contains("icon")||a.tagName==="I"),o=M(t).trim();return e&&!o}function Xt(t){const n=k(M(t));if(n)return`button "${n}"`;const e=P(t);if(e)return`button [${k(e)}]`;const o=t.getAttribute("title");if(o)return`button [${k(o)}]`;if(mt(t))return"icon button";const a=t.getAttribute("type");return a&&a!=="button"?`${a} button`:"button"}function Dt(t){const n=k(M(t));if(n)return`link "${n}"`;const e=P(t);if(e)return`link [${k(e)}]`;const o=t.getAttribute("href");if(o&&o!=="#")try{const a=new URL(o,window.location.origin);return a.origin===window.location.origin?`link to ${a.pathname}`:`link to ${a.hostname}`}catch{return`link to ${k(o,30)}`}return mt(t)?"icon link":"link"}function Nt(t){const n=t.type||"text",e=ot(t),o=t.placeholder,a=t.name,s=P(t);let r="";switch(e?r=`"${k(e)}"`:s?r=`[${k(s)}]`:o?r=`"${k(o)}"`:a&&(r=`[${a}]`),n){case"submit":return`submit button${r?" "+r:""}`;case"checkbox":return`checkbox${r?" "+r:""}`;case"radio":return`radio${r?" "+r:""}`;case"file":return`file input${r?" "+r:""}`;case"search":return`search input${r?" "+r:""}`;case"email":return`email input${r?" "+r:""}`;case"password":return`password input${r?" "+r:""}`;case"number":return`number input${r?" "+r:""}`;case"tel":return`phone input${r?" "+r:""}`;case"url":return`URL input${r?" "+r:""}`;case"date":case"datetime-local":case"time":return`${n} input${r?" "+r:""}`;case"range":return`slider${r?" "+r:""}`;case"color":return`color picker${r?" "+r:""}`;default:return`text input${r?" "+r:""}`}}function Ot(t){const n=ot(t),e=P(t),o=t.name;let a="";return n?a=` "${k(n)}"`:e?a=` [${k(e)}]`:o&&(a=` [${o}]`),`dropdown${a}`}function jt(t){const n=ot(t),e=P(t),o=t.placeholder,a=t.name;let s="";return n?s=` "${k(n)}"`:e?s=` [${k(e)}]`:o?s=` "${k(o)}"`:a&&(s=` [${a}]`),`text area${s}`}function Vt(t){const n=t.tagName.toLowerCase(),e=k(M(t));return e?`${n} "${e}"`:n}function _t(t,n){const e=k(M(t),50);return e?`${n}: "${e}"`:n}function Bt(t){const n=t.alt;if(n)return`image "${k(n)}"`;const e=P(t);if(e)return`image [${k(e)}]`;const o=t.src;if(o)try{const s=new URL(o).pathname.split("/").pop();if(s&&!s.includes("?"))return`image "${k(s,30)}"`}catch{}return"image"}function Wt(t){if(t.closest('button, a, [role="button"]'))return"icon";const e=P(t);if(e)return`graphic [${k(e)}]`;const o=t.querySelector("title");return o!=null&&o.textContent?`graphic "${k(o.textContent)}"`:"icon"}function Ut(t){const n=P(t);return n?`video [${k(n)}]`:"video"}function qt(t){const n=t.tagName==="TH",e=k(M(t),30),o=n?"table header":"table cell";return e?`${o}: "${e}"`:o}function Kt(t){const n=k(M(t),50);return n?`list item: "${n}"`:"list item"}function Gt(t){const n=k(M(t));return n?`label "${n}"`:"label"}function Zt(t){const n=t.getAttribute("role");if(n)return n;const e=Array.from(t.classList),o=["header","footer","nav","sidebar","main","content","article","section","card","modal","dialog","menu","dropdown","panel","container","wrapper"];for(const s of e){const r=s.toLowerCase();for(const i of o)if(r.includes(i))return i}const a=t.getAttribute("data-testid")||t.getAttribute("data-test-id");return a?a.replace(/[-_]/g," "):t.tagName.toLowerCase()}function j(t){const n=t.tagName.toLowerCase();if(n==="button"||t.getAttribute("role")==="button"||t instanceof HTMLInputElement&&(t.type==="button"||t.type==="submit"||t.type==="reset"))return Xt(t);if(n==="a")return Dt(t);if(n==="input")return Nt(t);if(n==="select")return Ot(t);if(n==="textarea")return jt(t);if(/^h[1-6]$/.test(n))return Vt(t);if(n==="p")return _t(t,"paragraph");if(n==="span"){const e=k(M(t));return e?`text: "${e}"`:"text"}if(n==="code"){const e=k(M(t),30);return e?`code: \`${e}\``:"code"}return n==="pre"?"code block":n==="blockquote"?"blockquote":n==="img"?Bt(t):n==="svg"?Wt(t):n==="video"?Ut(t):n==="audio"?"audio":n==="canvas"?"canvas":n==="iframe"?"iframe":n==="th"||n==="td"?qt(t):n==="tr"?"table row":n==="table"?"table":n==="li"?Kt(t):n==="ul"?"unordered list":n==="ol"?"ordered list":n==="label"?Gt(t):n==="nav"?"navigation":n==="header"?"header":n==="footer"?"footer":n==="main"?"main content":n==="aside"?"sidebar":n==="article"?"article":n==="section"?"section":n==="form"?"form":n==="figure"?"figure":n==="figcaption"?"caption":Zt(t)}const at=/[-_][a-zA-Z0-9]{5,}$/,st=[/^(.+?)[-_][a-zA-Z0-9]{5,}$/,/^sc-[a-zA-Z0-9]+$/,/^css-[a-zA-Z0-9]+$/,/^\[.+\]$/],gt=["text-","bg-","flex","grid","p-","px-","py-","m-","mx-","my-","w-","h-","min-","max-","border","rounded","shadow","opacity","font-","leading-","tracking-","space-","gap-","items-","justify-","self-","overflow-","z-","cursor-","transition","transform","scale-","rotate-","translate-","animate-","duration-","ease-","delay-","hidden","block","inline","relative","absolute","fixed","sticky","static","top-","right-","bottom-","left-","inset-"];function bt(t){const n=t.trim();if(!n)return null;if(gt.some(o=>n.startsWith(o)))return n;for(const o of st.slice(1))if(o.test(n))return null;const e=n.match(st[0]);return e?e[1]:at.test(n)?n.replace(at,""):n}function Jt(t){const n=Array.isArray(t)?t:Array.from(t),e=new Set;for(const o of n){const a=bt(o);a&&e.add(a)}return Array.from(e)}function vt(t){return Jt(t.classList).filter(e=>e.length>2)}function Qt(t){const n=vt(t);return n.find(o=>!gt.some(a=>o.startsWith(a)))||n[0]||null}const te=4,xt=new Set(["html","body","main","div","span"]),yt=new Set(["header","footer","nav","aside","article","section","form","table","ul","ol","dialog"]);function kt(t){const n=t.tagName.toLowerCase();if(t.id){const s=bt(t.id);if(s&&s===t.id)return`#${t.id}`}const e=Qt(t);if(yt.has(n))return e?`${n}.${e}`:n;if(e)return xt.has(n)?`.${e}`:`${n}.${e}`;const o=t.getAttribute("role");if(o)return`[role="${o}"]`;const a=t.getAttribute("data-testid")||t.getAttribute("data-test-id");if(a)return`[data-testid="${a}"]`;if((t instanceof HTMLInputElement||t instanceof HTMLSelectElement||t instanceof HTMLTextAreaElement)&&t.name)return`${n}[name="${t.name}"]`;if(t instanceof HTMLInputElement||t instanceof HTMLButtonElement){const s=t.type;if(s&&s!=="text"&&s!=="submit")return`${n}[type="${s}"]`}if(t instanceof HTMLAnchorElement&&t.href)try{const s=new URL(t.href);if(s.origin===window.location.origin&&s.pathname!=="/")return`a[href="${s.pathname}"]`}catch{}return n}function W(t,n){try{const e=document.querySelectorAll(t);return e.length===1&&e[0]===n}catch{return!1}}function ee(t){const n=t.parentElement;if(!n)return"";const e=Array.from(n.children).filter(a=>a.tagName===t.tagName);return e.length<=1?"":`:nth-of-type(${e.indexOf(t)+1})`}function ne(t){const n=[];let e=t,o=0;for(;e&&o<te;){const a=e.tagName.toLowerCase();if(a==="body"||a==="html")break;const s=kt(e);if(s.startsWith("#")){n.unshift(s);break}if(xt.has(a)&&s===a){e=e.parentElement;continue}if(n.unshift(s),o++,yt.has(a)&&o>=2)break;e=e.parentElement}return n}function oe(t){const n=kt(t);if(n.startsWith("#")||W(n,t))return n;const e=ne(t);if(e.length===0)return t.tagName.toLowerCase();let o=e.join(" > ");if(W(o,t))return o;const a=e[e.length-1],s=ee(t);return s&&(e[e.length-1]=a+s,o=e.join(" > "),W(o,t)),o}function ae(t){const n=[];let e=t;for(;e;){const o=e.tagName.toLowerCase();if(o==="html"){n.unshift("html");break}let a=o;e.id&&(a+=`#${e.id}`);const s=Array.from(e.classList).slice(0,3);s.length>0&&(a+="."+s.join("."));const r=e.parentElement;if(r){const i=Array.from(r.children);if(i.length>1){const d=i.indexOf(e)+1;a+=`:nth-child(${d})`}}n.unshift(a),e=e.parentElement}return n.join(" > ")}const se=["a[href]","button",'input:not([type="hidden"])',"select","textarea",'[tabindex]:not([tabindex="-1"])','[role="button"]','[role="link"]','[role="checkbox"]','[role="radio"]','[role="menuitem"]','[role="tab"]','[role="option"]','[role="switch"]','[role="slider"]','[role="textbox"]','[role="combobox"]','[contenteditable="true"]'];function re(t){for(const e of se)try{if(t.matches(e))return!0}catch{}return!!(t.hasAttribute("onclick")||t.hasAttribute("data-onclick")||window.getComputedStyle(t).cursor==="pointer")}function ie(t){const n=t.getAttribute("role");if(n)return n;const e=t.tagName.toLowerCase();return{a:t.hasAttribute("href")?"link":null,article:"article",aside:"complementary",button:"button",dialog:"dialog",footer:"contentinfo",form:"form",h1:"heading",h2:"heading",h3:"heading",h4:"heading",h5:"heading",h6:"heading",header:"banner",img:"img",input:le(t),li:"listitem",main:"main",nav:"navigation",ol:"list",option:"option",progress:"progressbar",section:t.hasAttribute("aria-label")||t.hasAttribute("aria-labelledby")?"region":null,select:"combobox",table:"table",tbody:"rowgroup",td:"cell",textarea:"textbox",th:"columnheader",thead:"rowgroup",tr:"row",ul:"list"}[e]||null}function le(t){const n=t.type;return{button:"button",checkbox:"checkbox",email:"textbox",image:"button",number:"spinbutton",radio:"radio",range:"slider",reset:"button",search:"searchbox",submit:"button",tel:"textbox",text:"textbox",url:"textbox"}[n]||"textbox"}function ce(t){return t.hasAttribute("tabindex")?t.tabIndex:t.matches('a[href], button, input, select, textarea, [contenteditable="true"]')?0:null}function Z(t){var o;if(!t)return null;const n=t.split(/\s+/),e=[];for(const a of n){const s=document.getElementById(a);if(s){const r=(o=s.textContent)==null?void 0:o.trim();r&&e.push(r)}}return e.length>0?e.join(" "):null}function ue(t){return{role:ie(t),ariaLabel:t.getAttribute("aria-label"),ariaDescribedBy:Z(t.getAttribute("aria-describedby")),ariaLabelledBy:Z(t.getAttribute("aria-labelledby")),tabIndex:ce(t),isInteractive:re(t)}}function de(t){const n=["banner","complementary","contentinfo","form","main","navigation","region","search"],e=["header","footer","nav","main","aside","form","section"];let o=t.parentElement;for(;o&&o!==document.body;){const a=o.getAttribute("role");if(a&&n.includes(a))return o;const s=o.tagName.toLowerCase();if(e.includes(s))if(s==="section"){if(o.hasAttribute("aria-label")||o.hasAttribute("aria-labelledby"))return o}else return o;o=o.parentElement}return null}function pe(t){if(!t)return null;const n=t.getAttribute("role")||t.tagName.toLowerCase(),e=t.getAttribute("aria-label");if(e)return`${n} "${e}"`;const o=t.getAttribute("aria-labelledby");if(o){const a=Z(o);if(a)return`${n} "${a}"`}return n}function fe(t){return t.replace(/([A-Z])/g,"-$1").toLowerCase()}function he(t){const n=window.getComputedStyle(t);return{display:n.display,position:n.position,visibility:n.visibility,opacity:n.opacity,zIndex:n.zIndex,overflow:n.overflow,pointerEvents:n.pointerEvents,cursor:n.cursor,backgroundColor:n.backgroundColor,color:n.color,fontSize:n.fontSize,fontFamily:n.fontFamily,fontWeight:n.fontWeight,lineHeight:n.lineHeight,padding:n.padding,margin:n.margin,border:n.border,borderRadius:n.borderRadius,boxShadow:n.boxShadow,transform:n.transform,transition:n.transition}}function me(t){return Object.entries(t).map(([n,e])=>`${fe(n)}: ${e}`).join(`
`)}function ge(t){let n=t;for(;n&&n!==document.body&&n!==document.documentElement;){const o=window.getComputedStyle(n).position;if(o==="fixed"||o==="sticky")return!0;n=n.parentElement}return!1}const rt=200;function be(t){const n=t.getBoundingClientRect();return{top:n.top,left:n.left,width:n.width,height:n.height,bottom:n.bottom,right:n.right}}function ve(t){const n=t.parentElement,e=t.previousElementSibling,o=t.nextElementSibling,a=de(t);return{parent:n?j(n):null,previousSibling:e?j(e):null,nextSibling:o?j(o):null,containingLandmark:pe(a)}}function xe(t){const n={},e=new Set(["class","style","id"]);for(const o of Array.from(t.attributes))e.has(o.name)||(n[o.name]=o.value);return n}function ye(t){const e=(t.textContent||"").trim().replace(/\s+/g," ");return e.length<=rt?e:e.slice(0,rt-3)+"..."}function B(t,n=!1){return{humanReadable:j(t),selectorPath:oe(t),fullDomPath:ae(t),tagName:t.tagName.toLowerCase(),id:t.id||null,classes:vt(t),rect:be(t),accessibility:ue(t),computedStyles:n?he(t):null,nearbyContext:ve(t),innerText:ye(t),attributes:xe(t),isFixed:ge(t)}}function ke(){return`scope-${Date.now()}-${Math.random().toString(36).slice(2,9)}`}function Se(t){return t.size===0?1:Math.max(...Array.from(t.values()).map(e=>e.number))+1}function we(t,n,e,o={}){const{selectedText:a=null,isMultiSelect:s=!1,includeForensic:r=!1,clickX:i=0,clickY:d=0}=o,h=Date.now(),u=B(t,r);return{id:ke(),number:Se(e),comment:n,elementInfo:u,element:t,createdAt:h,updatedAt:h,selectedText:a,isMultiSelect:s,clickX:i,clickY:d}}function $e(t,n){return{...t,comment:n,updatedAt:Date.now()}}function Ee(t,n){const e=new Map;for(const[o,a]of t)a.number>n?e.set(o,{...a,number:a.number-1}):e.set(o,a);return e}function Ae(t,n){return{addScope:(u,p,l)=>{const c=t.getState(),m=c.settings.outputLevel==="forensic",y=we(u,p,c.scopes,{...l,includeForensic:m}),b=new Map(c.scopes);return b.set(y.id,y),t.setState({scopes:b}),n.emit("scope:create",{scope:y}),y},updateScope:(u,p)=>{const l=t.getState(),c=l.scopes.get(u);if(!c)return null;const m=p.comment!==void 0?$e(c,p.comment):c,y=new Map(l.scopes);return y.set(u,m),t.setState({scopes:y}),n.emit("scope:update",{scope:m}),m},deleteScope:u=>{const p=t.getState(),l=p.scopes.get(u);if(!l)return!1;const c=l.number,m=new Map(p.scopes);m.delete(u);const y=Ee(m,c);return t.batch(()=>{t.setState({scopes:y,deletingMarkerId:u,renumberFrom:c}),setTimeout(()=>{t.setState({deletingMarkerId:null,renumberFrom:null})},300)}),n.emit("scope:delete",{id:u}),!0},clearAllScopes:()=>{const u=t.getState(),p=Array.from(u.scopes.values());return t.batch(()=>{t.setState({scopes:new Map,selectedAnnotationId:null,showClearedFeedback:!0}),setTimeout(()=>{t.setState({showClearedFeedback:!1})},2e3)}),n.emit("scopes:clear",{scopes:p}),p},selectScope:u=>{t.setState({selectedAnnotationId:u}),n.emit("scope:select",{id:u})},getScope:u=>t.getState().scopes.get(u),getAllScopes:()=>Array.from(t.getState().scopes.values()).sort((u,p)=>u.number-p.number),getScopeCount:()=>t.getState().scopes.size}}const Ce="annotation-scopes-",St="annotation-settings",Me=10080*60*1e3;function wt(){return Ce+window.location.pathname}function Ie(t){return{id:t.id,number:t.number,comment:t.comment,elementInfo:t.elementInfo,createdAt:t.createdAt,updatedAt:t.updatedAt,selectedText:t.selectedText,isMultiSelect:t.isMultiSelect,clickX:t.clickX,clickY:t.clickY}}function Te(t){return{...t,element:null}}function Le(t){const n=Date.now()-Me;return t.filter(e=>e.createdAt>n)}function Fe(t){try{const n=wt(),e=Array.from(t.values()).map(Ie);return localStorage.setItem(n,JSON.stringify(e)),!0}catch(n){return console.error("[Annotation] Failed to save scopes:",n),!1}}function ze(){try{const t=wt(),n=localStorage.getItem(t);if(!n)return new Map;const e=JSON.parse(n),o=Le(e);o.length!==e.length&&localStorage.setItem(t,JSON.stringify(o));const a=new Map;for(const s of o)a.set(s.id,Te(s));return a}catch(t){return console.error("[Annotation] Failed to load scopes:",t),new Map}}function Pe(t){try{return localStorage.setItem(St,JSON.stringify(t)),!0}catch(n){return console.error("[Annotation] Failed to save settings:",n),!1}}function Ye(){try{const t=localStorage.getItem(St);return t?JSON.parse(t):null}catch(t){return console.error("[Annotation] Failed to load settings:",t),null}}function Re(t,n=1e3){let e=null;const o=()=>{e!==null&&(clearTimeout(e),e=null),Fe(t())};return{save:()=>{e!==null&&clearTimeout(e),e=setTimeout(o,n)},flush:o,destroy:()=>{e!==null&&(clearTimeout(e),e=null)}}}const $t={toolbar:{activate:"Activate agent-ui-annotation",freeze:"Freeze animations",unfreeze:"Unfreeze animations",showMarkers:"Show markers",hideMarkers:"Hide markers",copyToClipboard:"Copy to clipboard",clearAll:"Clear all",toggleTheme:"Toggle theme",settings:"Settings",close:"Close",copiedFeedback:"Copied to clipboard!",clearedFeedback:"Cleared all scopes"},popup:{close:"Close",addFeedback:"Add your feedback...",addFeedbackMulti:"Add feedback for all selected elements...",cancel:"Cancel",delete:"Delete",save:"Save",addScope:"Add Scope",addScopes:"Add {{count}} Scopes",elementsSelected:"{{count}} elements selected",andMore:"...and {{count}} more"},settings:{title:"Settings",outputLevel:"Output Level",markerColor:"Marker Color",blockInteractions:"Block page interactions",blockInteractionsHint:"Prevent clicks from activating buttons/links while annotating",showTooltips:"Show tooltips",autoClearAfterCopy:"Auto-clear after copy",outputLevels:{compact:"Compact",standard:"Standard",detailed:"Detailed",forensic:"Forensic"}},colors:{purple:"Purple",blue:"Blue",cyan:"Cyan",green:"Green",yellow:"Yellow",orange:"Orange",red:"Red"},marker:{noComment:"(no comment)"},output:{pageFeedback:"Page Feedback",noScopes:"No scopes created.",viewport:"Viewport",scopes:"Scopes",location:"Location",selectedText:"Selected text",feedback:"Feedback",domPath:"DOM Path",selector:"Selector",elementDetails:"Element Details",tag:"Tag",id:"ID",classes:"Classes",attributes:"Attributes",textContent:"Text content",positionDimensions:"Position & Dimensions",boundingBox:"Bounding box",size:"Size",fixedPositioning:"Fixed positioning",accessibility:"Accessibility",role:"Role",interactive:"Interactive",ariaLabel:"ARIA Label",describedBy:"Described by",tabIndex:"Tab index",computedStyles:"Computed Styles",context:"Context",landmark:"Landmark",parent:"Parent",previousSibling:"Previous sibling",nextSibling:"Next sibling",multiSelectNote:"Created via multi-select",metadata:"Metadata",created:"Created",updated:"Updated",environment:"Environment",url:"URL",devicePixelRatio:"Device pixel ratio",scrollPosition:"Scroll position",timestamp:"Timestamp",userAgent:"User agent",totalScopes:"Total scopes",positioning:"Positioning",fixedSticky:"Fixed/Sticky",yes:"Yes",no:"No",none:"none"}};let He=$t;const J=$t;function V(t,n){const e=n.split(".");let o=t;for(const a of e){if(o==null||typeof o!="object")return;o=o[a]}return typeof o=="string"?o:void 0}function _(t,n){return n?t.replace(/\{\{(\w+)\}\}/g,(e,o)=>{const a=n[o];return a!==void 0?String(a):`{{${o}}}`}):t}function x(t,n){const e=V(He,t);if(e===void 0){const o=V(J,t);return o===void 0?(console.warn(`[i18n] Missing translation for key: ${t}`),t):_(o,n)}return _(e,n)}function f(t,n){const o=V(J,t);if(o===void 0){const a=V(J,t);return a===void 0?(console.warn(`[i18n] Missing translation for key: ${t}`),t):_(a,n)}return _(o,n)}function Xe(){return{userAgent:navigator.userAgent,viewport:{width:window.innerWidth,height:window.innerHeight},devicePixelRatio:window.devicePixelRatio,url:window.location.href,timestamp:new Date().toISOString(),scrollPosition:{x:window.scrollX,y:window.scrollY}}}function De(t){const n=t.elementInfo.humanReadable,e=t.comment||f("marker.noComment");return`${t.number}. **${n}**: ${e}`}function Ne(t){const n=[];return n.push(`### ${t.number}. ${t.elementInfo.humanReadable}`),n.push(`**${f("output.location")}:** ${t.elementInfo.selectorPath}`),t.selectedText&&n.push(`**${f("output.selectedText")}:** "${t.selectedText}"`),n.push(`**${f("output.feedback")}:** ${t.comment||f("marker.noComment")}`),n.join(`
`)}function Oe(t){const n=[],e=t.elementInfo;n.push(`### ${t.number}. ${e.humanReadable}`),n.push(""),n.push(`**${f("output.location")}:** \`${e.selectorPath}\``),e.id&&n.push(`**${f("output.id")}:** ${e.id}`),e.classes.length>0&&n.push(`**${f("output.classes")}:** ${e.classes.join(", ")}`);const o=e.rect;n.push(`**Position:** ${Math.round(o.left)}x${Math.round(o.top)}, ${Math.round(o.width)}×${Math.round(o.height)}px`),e.isFixed&&n.push(`**${f("output.positioning")}:** ${f("output.fixedSticky")}`),t.selectedText&&n.push(`**${f("output.selectedText")}:** "${t.selectedText}"`);const a=e.nearbyContext;return(a.parent||a.containingLandmark)&&(n.push(""),n.push(`**${f("output.context")}:**`),a.containingLandmark&&n.push(`- ${f("output.landmark")}: ${a.containingLandmark}`),a.parent&&n.push(`- ${f("output.parent")}: ${a.parent}`),a.previousSibling&&n.push(`- Previous: ${a.previousSibling}`),a.nextSibling&&n.push(`- Next: ${a.nextSibling}`)),n.push(""),n.push(`**${f("output.feedback")}:** ${t.comment||f("marker.noComment")}`),n.join(`
`)}function je(t,n){const e=[],o=t.elementInfo;e.push(`### ${t.number}. ${o.humanReadable}`),e.push(""),e.push(`#### ${f("output.domPath")}`),e.push("```"),e.push(o.fullDomPath),e.push("```"),e.push(""),e.push(`**${f("output.selector")}:** \`${o.selectorPath}\``),e.push(""),e.push(`#### ${f("output.elementDetails")}`),e.push(`- **${f("output.tag")}:** ${o.tagName}`),o.id&&e.push(`- **${f("output.id")}:** ${o.id}`),o.classes.length>0&&e.push(`- **${f("output.classes")}:** ${o.classes.join(", ")}`);const a=Object.entries(o.attributes);if(a.length>0){e.push(`- **${f("output.attributes")}:**`);for(const[d,h]of a.slice(0,10))e.push(`  - ${d}: "${h}"`)}o.innerText&&e.push(`- **${f("output.textContent")}:** "${o.innerText}"`),e.push(""),e.push(`#### ${f("output.positionDimensions")}`);const s=o.rect;e.push(`- **${f("output.boundingBox")}:** (${Math.round(s.left)}, ${Math.round(s.top)}) to (${Math.round(s.right)}, ${Math.round(s.bottom)})`),e.push(`- **${f("output.size")}:** ${Math.round(s.width)}×${Math.round(s.height)}px`),e.push(`- **${f("output.fixedPositioning")}:** ${o.isFixed?f("output.yes"):f("output.no")}`),e.push(""),e.push(`#### ${f("output.accessibility")}`);const r=o.accessibility;e.push(`- **${f("output.role")}:** ${r.role||f("output.none")}`),e.push(`- **${f("output.interactive")}:** ${r.isInteractive?f("output.yes"):f("output.no")}`),r.ariaLabel&&e.push(`- **${f("output.ariaLabel")}:** "${r.ariaLabel}"`),r.ariaDescribedBy&&e.push(`- **${f("output.describedBy")}:** "${r.ariaDescribedBy}"`),r.tabIndex!==null&&e.push(`- **${f("output.tabIndex")}:** ${r.tabIndex}`),e.push(""),o.computedStyles&&(e.push(`#### ${f("output.computedStyles")}`),e.push("```css"),e.push(me(o.computedStyles)),e.push("```"),e.push(""));const i=o.nearbyContext;return e.push(`#### ${f("output.context")}`),i.containingLandmark&&e.push(`- **${f("output.landmark")}:** ${i.containingLandmark}`),i.parent&&e.push(`- **${f("output.parent")}:** ${i.parent}`),i.previousSibling&&e.push(`- **${f("output.previousSibling")}:** ${i.previousSibling}`),i.nextSibling&&e.push(`- **${f("output.nextSibling")}:** ${i.nextSibling}`),e.push(""),t.selectedText&&(e.push(`**${f("output.selectedText")}:** "${t.selectedText}"`),e.push("")),t.isMultiSelect&&(e.push(`*${f("output.multiSelectNote")}*`),e.push("")),e.push(`#### ${f("output.metadata")}`),e.push(`- **${f("output.created")}:** ${new Date(t.createdAt).toISOString()}`),e.push(`- **${f("output.updated")}:** ${new Date(t.updatedAt).toISOString()}`),e.push(""),e.push(`#### ${f("output.feedback")}`),e.push(t.comment||f("marker.noComment")),e.join(`
`)}function Ve(t,n){const e=[],o=window.location.pathname;return e.push(`## ${f("output.pageFeedback")}: ${o}`),t==="compact"?(e.push(""),e.join(`
`)):(e.push(`**${f("output.viewport")}:** ${window.innerWidth}×${window.innerHeight}`),e.push(`**${f("output.scopes")}:** ${n}`),e.push(""),e.join(`
`))}function _e(t,n){const e=[];return e.push(`## ${f("output.pageFeedback")}: ${t.url}`),e.push(""),e.push(`### ${f("output.environment")}`),e.push(`- **${f("output.url")}:** ${t.url}`),e.push(`- **${f("output.viewport")}:** ${t.viewport.width}×${t.viewport.height}`),e.push(`- **${f("output.devicePixelRatio")}:** ${t.devicePixelRatio}`),e.push(`- **${f("output.scrollPosition")}:** (${t.scrollPosition.x}, ${t.scrollPosition.y})`),e.push(`- **${f("output.timestamp")}:** ${t.timestamp}`),e.push(`- **${f("output.userAgent")}:** ${t.userAgent}`),e.push(`- **${f("output.totalScopes")}:** ${n}`),e.push(""),e.push("---"),e.push(""),e.join(`
`)}function it(t,n){if(t.length===0)return`## ${f("output.pageFeedback")}

${f("output.noScopes")}`;const e=[...t].sort((s,r)=>s.number-r.number),o=n==="forensic"?Xe():null,a=[];n==="forensic"&&o?a.push(_e(o,t.length)):a.push(Ve(n,t.length));for(const s of e){switch(n){case"compact":a.push(De(s));break;case"standard":a.push(Ne(s));break;case"detailed":a.push(Oe(s));break;case"forensic":a.push(je(s));break}n!=="compact"&&(a.push(""),a.push("---"),a.push(""))}return n==="compact"?a.join(`
`):a.join(`
`).trim()}async function Be(t){try{return await navigator.clipboard.writeText(t),!0}catch(n){try{const e=document.createElement("textarea");e.value=t,e.style.position="fixed",e.style.left="-9999px",document.body.appendChild(e),e.select();const o=document.execCommand("copy");return document.body.removeChild(e),o}catch{return console.error("[Annotation] Failed to copy to clipboard:",n),!1}}}const Q="data-annotation-toolbar",tt="data-annotation-marker",et="data-annotation-popup",nt="data-annotation-settings";function R(t){return t?t.tagName.toLowerCase()==="agent-ui-annotation"||t.closest("agent-ui-annotation")?!0:t.hasAttribute(Q)||t.hasAttribute(tt)||t.hasAttribute(et)||t.hasAttribute(nt)||t.closest(`[${Q}], [${tt}], [${et}], [${nt}]`)!==null:!1}function We(t){const n=t.composedPath();for(const e of n)if(e instanceof Element&&(e.tagName.toLowerCase()==="agent-ui-annotation"||e.hasAttribute&&(e.hasAttribute(Q)||e.hasAttribute(tt)||e.hasAttribute(et)||e.hasAttribute(nt))))return!0;return!1}function Ue(t){const n=t.target;return R(n)?null:n}function qe(t,n){let e=!1;const o=p=>{const l=t.getState();if(l.mode==="disabled"||We(p)||l.settingsPanelVisible)return;const c=Ue(p);if(!c)return;l.settings.blockInteractions&&c.matches('a, button, input, select, textarea, [role="button"], [onclick]')&&(p.preventDefault(),p.stopPropagation());const m=l.settings.outputLevel==="forensic",y=B(c,m),b=p.clientX,v=y.isFixed?p.clientY:p.clientY+window.scrollY;n.emit("element:click",{element:c,elementInfo:y,clickX:b,clickY:v})},a=p=>{if(t.getState().mode!=="multi-select")return;const c=p.target;if(R(c))return;const m={x:p.clientX,y:p.clientY};n.emit("multiselect:start",{position:m})},s=p=>{const l=t.getState();if(!(!l.isSelecting&&l.selectionRect===null)&&l.isSelecting&&l.selectionRect){const c={startX:l.selectionRect.startX,startY:l.selectionRect.startY,endX:p.clientX,endY:p.clientY};n.emit("multiselect:update",{rect:c})}},r=p=>{const l=t.getState();if(!l.isSelecting)return;const c=l.selectionRect;if(!c)return;const m=Ke(c);n.emit("multiselect:end",{elements:m})},i=()=>{t.setState({scrollY:window.scrollY})},d=p=>{const l=t.getState();p.key==="Escape"&&(l.popupVisible?(t.setState({popupVisible:!1,popupAnnotationId:null}),p.preventDefault()):l.isSelecting?(t.setState({isSelecting:!1,selectionRect:null}),p.preventDefault()):l.mode!=="disabled"&&(n.emit("deactivate",void 0),p.preventDefault()))};return{attach:()=>{e||(document.addEventListener("click",o,!0),document.addEventListener("mousedown",a,!0),document.addEventListener("mousemove",s,!0),document.addEventListener("mouseup",r,!0),document.addEventListener("scroll",i,{passive:!0}),document.addEventListener("keydown",d,!0),e=!0)},detach:()=>{e&&(document.removeEventListener("click",o,!0),document.removeEventListener("mousedown",a,!0),document.removeEventListener("mousemove",s,!0),document.removeEventListener("mouseup",r,!0),document.removeEventListener("scroll",i),document.removeEventListener("keydown",d,!0),e=!1)},isActive:()=>e}}function Ke(t){const n=Math.min(t.startX,t.endX),e=Math.max(t.startX,t.endX),o=Math.min(t.startY,t.endY),a=Math.max(t.startY,t.endY),r=document.querySelectorAll("button, a, input, img, p, h1, h2, h3, h4, h5, h6, li, label, td, th"),i={width:window.innerWidth,height:window.innerHeight},d=[];for(const h of r){if(R(h))continue;const u=h.getBoundingClientRect();u.right<n||u.left>e||u.bottom<o||u.top>a||u.width>i.width*.8&&u.height>i.height*.5||u.width<10||u.height<10||d.push(h)}return d.filter(h=>!d.some(u=>u!==h&&h.contains(u)))}function Ge(t,n,e={}){const{leading:o=!0,trailing:a=!0}=e;let s=null,r=null,i=null,d=0;const h=v=>{d=v;const S=r;r=null,t(...S)},u=v=>{const S=i!==null?v-i:0,$=v-d;return i===null||S>=n||S<0||$>=n},p=v=>{const S=i!==null?v-i:0,$=n-S;return Math.max(0,$)},l=()=>{const v=Date.now();if(u(v))return c(v);s=setTimeout(l,p(v))},c=v=>{s=null,a&&r&&h(v),r=null},m=()=>{s!==null&&clearTimeout(s),d=0,r=null,i=null,s=null},y=()=>{s!==null&&c(Date.now())},b=(...v)=>{const S=Date.now(),$=u(S);r=v,i=S,$&&s===null&&(o&&h(S),s=setTimeout(l,n))};return b.cancel=m,b.flush=y,b}const Ze=50;function Je(t,n){let e=!1,o=null;const s=Ge(u=>{const p=t.getState();if(p.mode==="disabled"||p.isSelecting){p.hoveredElement!==null&&(t.setState({hoveredElement:null,hoveredElementInfo:null}),n.emit("element:hover",{element:null,elementInfo:null}));return}if(p.popupVisible||p.settingsPanelVisible)return;const l=u.target;if(R(l)){o!==null&&(o=null,t.setState({hoveredElement:null,hoveredElementInfo:null}),n.emit("element:hover",{element:null,elementInfo:null}));return}if(l===o)return;o=l;const c=p.settings.outputLevel==="forensic",m=B(l,c);t.setState({hoveredElement:l,hoveredElementInfo:m}),n.emit("element:hover",{element:l,elementInfo:m})},Ze,{leading:!0,trailing:!0}),r=u=>{const p=u.relatedTarget;p&&document.documentElement.contains(p)||(o=null,t.setState({hoveredElement:null,hoveredElementInfo:null}),n.emit("element:hover",{element:null,elementInfo:null}))};return{attach:()=>{e||(document.addEventListener("mousemove",s,{passive:!0}),document.addEventListener("mouseleave",r),e=!0)},detach:()=>{e&&(document.removeEventListener("mousemove",s),document.removeEventListener("mouseleave",r),s.cancel(),o=null,t.setState({hoveredElement:null,hoveredElementInfo:null}),e=!1)},clearHover:()=>{o=null,t.setState({hoveredElement:null,hoveredElementInfo:null}),n.emit("element:hover",{element:null,elementInfo:null})},isActive:()=>e}}const Qe=8,lt=20;function tn(t,n){let e=null,o=!1,a=!1;const s=()=>{document.body.style.userSelect="none",document.body.style.webkitUserSelect="none"},r=()=>{document.body.style.userSelect="",document.body.style.webkitUserSelect=""},i=b=>{e=b,o=!1},d=b=>{if(!e)return;const v=b.clientX-e.x,S=b.clientY-e.y,$=Math.sqrt(v*v+S*S);if(!o&&$>Qe){o=!0,s();const I={startX:e.x,startY:e.y,endX:b.clientX,endY:b.clientY};t.setState({isSelecting:!0,selectionRect:I,selectionPreviewElements:U(I)})}if(o){const I={startX:e.x,startY:e.y,endX:b.clientX,endY:b.clientY};t.setState({selectionRect:I,selectionPreviewElements:U(I)})}},h=()=>{const b=t.getState(),v=b.selectionRect,S=b.selectionPreviewElements;if(e=null,o=!1,r(),t.setState({isSelecting:!1,selectionRect:null,selectionPreviewElements:[]}),!v)return[];const $=Math.abs(v.endX-v.startX),I=Math.abs(v.endY-v.startY);return $<lt&&I<lt?[]:S.length>0?S:U(v)},u=()=>{e=null,o=!1,r(),t.setState({isSelecting:!1,selectionRect:null,selectionPreviewElements:[]})},p=b=>{const v=t.getState();if(v.mode!=="select"&&v.mode!=="multi-select"||v.popupVisible)return;const S=b.target;R(S)||b.button===0&&i({x:b.clientX,y:b.clientY})},l=b=>{e&&d(b)},c=()=>{if(!e)return;const b=h();b.length>0&&n.emit("multiselect:end",{elements:b})};return{attach:()=>{a||(document.addEventListener("mousedown",p,!0),document.addEventListener("mousemove",l,!0),document.addEventListener("mouseup",c,!0),a=!0)},detach:()=>{a&&(document.removeEventListener("mousedown",p,!0),document.removeEventListener("mousemove",l,!0),document.removeEventListener("mouseup",c,!0),u(),a=!1)},cancel:u,isActive:()=>a,isDragging:()=>o}}function U(t){const n=Math.min(t.startX,t.endX),e=Math.max(t.startX,t.endX),o=Math.min(t.startY,t.endY),a=Math.max(t.startY,t.endY),r=document.querySelectorAll("button, a, input, img, p, h1, h2, h3, h4, h5, h6, li, label, td, th"),i={width:window.innerWidth,height:window.innerHeight},d=[];for(const h of r){if(R(h))continue;const u=h.getBoundingClientRect();!(u.right>=n&&u.left<=e&&u.bottom>=o&&u.top<=a)||u.width>i.width*.8&&u.height>i.height*.5||u.width<10||u.height<10||d.push(h)}return d.filter(h=>!d.some(u=>u!==h&&h.contains(u)))}function en(t){const n=Math.min(t.startX,t.endX),e=Math.min(t.startY,t.endY),o=Math.abs(t.endX-t.startX),a=Math.abs(t.endY-t.startY);return{x:n,y:e,width:o,height:a}}const nn="annotation-freeze-styles",on=`
  *:not([data-annotation-toolbar] *):not([data-annotation-marker] *):not([data-annotation-popup] *) {
    animation-play-state: paused !important;
    transition: none !important;
  }
`;function an(t,n){let e=!1,o=null,a=new WeakSet;const s=()=>{o||(o=document.createElement("style"),o.id=nn,o.textContent=on,document.head.appendChild(o))},r=()=>{o&&(o.remove(),o=null)},i=()=>{const c=document.querySelectorAll("video");for(const m of c)m.paused||(a.add(m),m.pause())},d=()=>{const c=document.querySelectorAll("video");for(const m of c)a.has(m)&&m.play().catch(()=>{});a=new WeakSet},h=()=>{e||(s(),i(),e=!0,t.setState({isFrozen:!0}),n.emit("freeze:toggle",{frozen:!0}))},u=()=>{e&&(r(),d(),e=!1,t.setState({isFrozen:!1}),n.emit("freeze:toggle",{frozen:!1}))};return{freeze:h,unfreeze:u,toggle:()=>{e?u():h()},destroy:()=>{e&&u()},isFrozen:()=>e}}const sn="annotation-cursor-styles",rn=`
  /* Crosshair for most elements */
  body:not([data-annotation-disabled]) *:not([data-annotation-toolbar] *):not([data-annotation-marker] *):not([data-annotation-popup] *) {
    cursor: crosshair !important;
  }

  /* Text cursor for text selection */
  body:not([data-annotation-disabled]) p:not([data-annotation-toolbar] *),
  body:not([data-annotation-disabled]) span:not([data-annotation-toolbar] *),
  body:not([data-annotation-disabled]) h1:not([data-annotation-toolbar] *),
  body:not([data-annotation-disabled]) h2:not([data-annotation-toolbar] *),
  body:not([data-annotation-disabled]) h3:not([data-annotation-toolbar] *),
  body:not([data-annotation-disabled]) h4:not([data-annotation-toolbar] *),
  body:not([data-annotation-disabled]) h5:not([data-annotation-toolbar] *),
  body:not([data-annotation-disabled]) h6:not([data-annotation-toolbar] *),
  body:not([data-annotation-disabled]) li:not([data-annotation-toolbar] *),
  body:not([data-annotation-disabled]) td:not([data-annotation-toolbar] *),
  body:not([data-annotation-disabled]) th:not([data-annotation-toolbar] *),
  body:not([data-annotation-disabled]) code:not([data-annotation-toolbar] *),
  body:not([data-annotation-disabled]) pre:not([data-annotation-toolbar] *) {
    cursor: text !important;
  }

  /* Pointer for Annotation UI elements */
  [data-annotation-marker],
  [data-annotation-marker] *,
  [data-annotation-toolbar] button,
  [data-annotation-popup] button {
    cursor: pointer !important;
  }

  /* Default for toolbar */
  [data-annotation-toolbar],
  [data-annotation-toolbar] *,
  [data-annotation-popup],
  [data-annotation-popup] * {
    cursor: default !important;
  }

  /* Crosshair for multi-select mode */
  body[data-annotation-multiselect] *:not([data-annotation-toolbar] *):not([data-annotation-marker] *):not([data-annotation-popup] *) {
    cursor: crosshair !important;
  }

  /* Move cursor when dragging toolbar */
  body[data-annotation-dragging] * {
    cursor: move !important;
  }
`;let z=null;function ln(){z||(z=document.createElement("style"),z.id=sn,z.textContent=rn,document.head.appendChild(z))}function cn(){z&&(z.remove(),z=null)}function q(t){t?document.body.setAttribute("data-annotation-multiselect",""):document.body.removeAttribute("data-annotation-multiselect")}function un(t){document.body.removeAttribute("data-annotation-disabled")}function dn(){cn(),document.body.removeAttribute("data-annotation-multiselect"),document.body.removeAttribute("data-annotation-dragging"),document.body.removeAttribute("data-annotation-disabled")}function pn(t={}){const{settings:n,loadPersisted:e=!0,onScopeCreate:o,onScopeUpdate:a,onScopeDelete:s,onScopesClear:r,onCopy:i,copyToClipboard:d=!0}=t,h=e?Ye():null,u=e?ze():new Map,p={...ht,...h,...n},l=zt(Rt({settings:p,scopes:u})),c=Pt(),m=Ae(l,c),y=an(l,c),b=qe(l,c),v=Je(l,c),S=tn(l,c),$=Re(()=>l.getState().scopes,1e3);o&&c.on("scope:create",({scope:g})=>o(g)),a&&c.on("scope:update",({scope:g})=>a(g)),s&&c.on("scope:delete",({id:g})=>s(g)),r&&c.on("scopes:clear",({scopes:g})=>r(g)),c.on("scope:create",()=>$.save()),c.on("scope:update",()=>$.save()),c.on("scope:delete",()=>$.save()),c.on("scopes:clear",()=>$.save()),c.on("settings:change",({settings:g})=>{const w=l.getState().settings;Pe({...w,...g})}),c.on("element:click",({element:g,elementInfo:w,clickX:C,clickY:T})=>{if(l.getState().mode==="disabled")return;const Y=w.isFixed?T:T-window.scrollY;l.setState({popupVisible:!0,popupAnnotationId:null,popupElementInfo:w,popupClickX:C,popupClickY:Y,pendingMarkerX:C,pendingMarkerY:T,pendingMarkerIsFixed:w.isFixed,hoveredElement:g,hoveredElementInfo:w})}),c.on("multiselect:end",({elements:g})=>{if(g.length===0)return;const C=l.getState().settings.outputLevel==="forensic",T=g.map(L=>B(L,C)),F=g.map(L=>L.getBoundingClientRect()),Y=Math.min(...F.map(L=>L.left)),At=Math.max(...F.map(L=>L.right)),Ct=Math.min(...F.map(L=>L.top)),Mt=Math.max(...F.map(L=>L.bottom)),It=(Y+At)/2,Tt=(Ct+Mt)/2;l.setState({popupVisible:!0,popupAnnotationId:null,popupElementInfo:T[0],popupClickX:It,popupClickY:Tt,pendingMarkerX:0,pendingMarkerY:0,pendingMarkerIsFixed:!1,multiSelectElements:g,multiSelectInfos:T,hoveredElement:g[0],hoveredElementInfo:T[0]})});const I=(g="select")=>{l.getState().mode==="disabled"&&(l.batch(()=>{l.setState({mode:g,toolbarExpanded:!0,markersVisible:!0,scrollY:window.scrollY})}),b.attach(),v.attach(),S.attach(),ln(),un(),g==="multi-select"&&q(!0),c.emit("activate",void 0),c.emit("mode:change",{mode:g}))},D=()=>{const g=l.getState();g.mode!=="disabled"&&(l.batch(()=>{l.setState({mode:"disabled",toolbarExpanded:!1,popupVisible:!1,popupAnnotationId:null,isSelecting:!1,selectionRect:null})}),b.detach(),v.detach(),S.detach(),dn(),g.isFrozen&&y.unfreeze(),c.emit("deactivate",void 0),c.emit("mode:change",{mode:"disabled"}))};return{store:l,eventBus:c,scopes:m,freeze:y,activate:I,deactivate:D,toggle:()=>{l.getState().mode==="disabled"?I():D()},isActive:()=>l.getState().mode!=="disabled",setMode:g=>{const w=l.getState();if(g==="disabled"){D();return}if(w.mode==="disabled"){I(g);return}g==="multi-select"&&w.mode!=="multi-select"?(S.attach(),q(!0)):g==="select"&&w.mode==="multi-select"&&(S.detach(),q(!1)),l.setState({mode:g}),c.emit("mode:change",{mode:g})},getMode:()=>l.getState().mode,updateSettings:g=>{const C={...l.getState().settings,...g};l.setState({settings:C}),c.emit("settings:change",{settings:g})},getSettings:()=>l.getState().settings,copyOutput:async g=>{const w=l.getState(),C=g||w.settings.outputLevel,T=m.getAllScopes(),F=it(T,C);let Y=!0;return d&&(Y=await Be(F)),Y&&(l.setState({showCopiedFeedback:!0}),setTimeout(()=>{l.setState({showCopiedFeedback:!1})},2e3),i&&i(F,C),c.emit("output:copy",{content:F,level:C}),w.settings.autoClearAfterCopy&&m.clearAllScopes()),Y},getOutput:g=>{const w=l.getState(),C=g||w.settings.outputLevel,T=m.getAllScopes();return it(T,C)},showPopup:g=>{if(g){const w=l.getState().scopes.get(g);if(w){l.setState({popupVisible:!0,popupAnnotationId:g,popupElementInfo:w.elementInfo,popupClickX:w.clickX,popupClickY:w.clickY});return}}l.setState({popupVisible:!0,popupAnnotationId:g||null})},hidePopup:()=>{l.setState({popupVisible:!1,popupAnnotationId:null,popupElementInfo:null,popupClickX:0,popupClickY:0,pendingMarkerX:0,pendingMarkerY:0,pendingMarkerIsFixed:!1,multiSelectElements:[],multiSelectInfos:[]})},subscribe:g=>l.subscribe(g),destroy:()=>{D(),$.flush(),$.destroy(),y.destroy(),c.destroy(),l.destroy()}}}const fn={"--as-bg-primary":"rgba(255, 255, 255, 0.95)","--as-bg-secondary":"rgba(245, 245, 245, 0.95)","--as-bg-hover":"rgba(0, 0, 0, 0.05)","--as-bg-active":"rgba(0, 0, 0, 0.1)","--as-bg-overlay":"rgba(255, 255, 255, 0.8)","--as-text-primary":"#1a1a1a","--as-text-secondary":"#666666","--as-text-muted":"#999999","--as-text-inverse":"#ffffff","--as-border-primary":"rgba(0, 0, 0, 0.1)","--as-border-secondary":"rgba(0, 0, 0, 0.05)","--as-accent":"#AF52DE","--as-accent-hover":"#9B47C7","--as-accent-light":"rgba(175, 82, 222, 0.1)","--as-success":"#34C759","--as-warning":"#FF9500","--as-error":"#FF3B30","--as-shadow-sm":"0 1px 2px rgba(0, 0, 0, 0.05)","--as-shadow-md":"0 4px 12px rgba(0, 0, 0, 0.1)","--as-shadow-lg":"0 8px 24px rgba(0, 0, 0, 0.15)","--as-backdrop-blur":"blur(12px)"},ct={"--as-bg-primary":"rgba(24, 24, 27, 0.95)","--as-bg-secondary":"rgba(39, 39, 42, 0.95)","--as-bg-hover":"rgba(255, 255, 255, 0.1)","--as-bg-active":"rgba(255, 255, 255, 0.15)","--as-bg-overlay":"rgba(24, 24, 27, 0.8)","--as-text-primary":"#ffffff","--as-text-secondary":"#a1a1aa","--as-text-muted":"#71717a","--as-text-inverse":"#1a1a1a","--as-border-primary":"rgba(255, 255, 255, 0.1)","--as-border-secondary":"rgba(255, 255, 255, 0.05)","--as-accent":"#AF52DE","--as-accent-hover":"#C77DFF","--as-accent-light":"rgba(175, 82, 222, 0.2)","--as-success":"#34C759","--as-warning":"#FF9500","--as-error":"#FF3B30","--as-shadow-sm":"0 1px 2px rgba(0, 0, 0, 0.2)","--as-shadow-md":"0 4px 12px rgba(0, 0, 0, 0.3)","--as-shadow-lg":"0 8px 24px rgba(0, 0, 0, 0.4)","--as-backdrop-blur":"blur(12px)"},hn={"--as-space-xs":"4px","--as-space-sm":"8px","--as-space-md":"12px","--as-space-lg":"16px","--as-space-xl":"24px","--as-radius-sm":"4px","--as-radius-md":"8px","--as-radius-lg":"12px","--as-radius-full":"9999px","--as-font-family":'-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif',"--as-font-mono":'ui-monospace, SFMono-Regular, "SF Mono", Menlo, monospace',"--as-font-size-xs":"10px","--as-font-size-sm":"12px","--as-font-size-md":"14px","--as-font-size-lg":"16px","--as-transition-fast":"100ms ease","--as-transition-normal":"200ms ease","--as-transition-slow":"300ms ease","--as-z-toolbar":"999999","--as-z-markers":"999998","--as-z-popup":"1000000","--as-z-tooltip":"1000001","--as-z-overlay":"999997"};function K(t){return t==="auto"?window.matchMedia("(prefers-color-scheme: dark)").matches?"dark":"light":t}function N(t){return Object.entries(t).map(([n,e])=>`${n}: ${e};`).join(`
  `)}const mn=`
  /* CSS Variables */
  :host {
    ${N(hn)}
    ${N(fn)}
  }

  :host([data-theme="dark"]) {
    ${N(ct)}
  }

  @media (prefers-color-scheme: dark) {
    :host([data-theme="auto"]) {
      ${N(ct)}
    }
  }

  /* Reset */
  *,
  *::before,
  *::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  /* Base styles */
  :host {
    all: initial;
    font-family: var(--as-font-family);
    font-size: var(--as-font-size-md);
    color: var(--as-text-primary);
    line-height: 1.5;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  /* Toolbar container */
  .toolbar {
    position: fixed;
    z-index: var(--as-z-toolbar);
    display: flex;
    align-items: center;
    gap: var(--as-space-sm);
    padding: var(--as-space-sm) var(--as-space-md);
    background: var(--as-bg-primary);
    border: 1px solid var(--as-border-primary);
    border-radius: var(--as-radius-full);
    box-shadow: var(--as-shadow-lg);
    backdrop-filter: var(--as-backdrop-blur);
    user-select: none;
    transition: transform var(--as-transition-normal), opacity var(--as-transition-normal);
  }

  .toolbar.collapsed {
    padding: var(--as-space-sm);
  }

  .toolbar.dragging {
    cursor: move;
    opacity: 0.9;
  }

  /* Toolbar entrance animation */
  .toolbar.entering {
    animation: toolbar-enter 0.3s ease-out;
  }

  @keyframes toolbar-enter {
    from {
      opacity: 0;
      transform: scale(0.9) translateY(10px);
    }
    to {
      opacity: 1;
      transform: scale(1) translateY(0);
    }
  }

  /* Toolbar buttons */
  .toolbar-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 32px;
    height: 32px;
    padding: 0;
    background: transparent;
    border: none;
    border-radius: var(--as-radius-md);
    color: var(--as-text-primary);
    cursor: pointer;
    transition: background var(--as-transition-fast), color var(--as-transition-fast);
  }

  .toolbar-btn:hover {
    background: var(--as-bg-hover);
  }

  .toolbar-btn:active {
    background: var(--as-bg-active);
  }

  .toolbar-btn.active {
    background: var(--as-accent-light);
    color: var(--as-accent);
  }

  .toolbar-btn svg {
    width: 18px;
    height: 18px;
  }

  /* Toggle button (collapsed state) */
  .toggle-btn {
    position: relative;
    width: 36px;
    height: 36px;
  }

  .toggle-btn .badge {
    position: absolute;
    top: -4px;
    right: -4px;
    min-width: 16px;
    height: 16px;
    padding: 0 4px;
    background: var(--as-accent);
    border-radius: var(--as-radius-full);
    color: var(--as-text-inverse);
    font-size: var(--as-font-size-xs);
    font-weight: 600;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  /* Separator */
  .separator {
    width: 1px;
    height: 20px;
    background: var(--as-border-primary);
    margin: 0 var(--as-space-xs);
  }

  /* Scope count */
  .scope-count {
    display: flex;
    align-items: center;
    gap: var(--as-space-xs);
    padding: 0 var(--as-space-sm);
    font-size: var(--as-font-size-sm);
    font-weight: 500;
    color: var(--as-text-secondary);
  }

  .scope-count .count {
    color: var(--as-text-primary);
    font-weight: 600;
  }

  /* Feedback toast */
  .feedback {
    position: absolute;
    top: -40px;
    left: 50%;
    transform: translateX(-50%);
    padding: var(--as-space-sm) var(--as-space-md);
    background: var(--as-bg-primary);
    border: 1px solid var(--as-border-primary);
    border-radius: var(--as-radius-md);
    box-shadow: var(--as-shadow-md);
    font-size: var(--as-font-size-sm);
    white-space: nowrap;
    animation: feedback-enter 0.2s ease-out;
  }

  @keyframes feedback-enter {
    from {
      opacity: 0;
      transform: translateX(-50%) translateY(10px);
    }
    to {
      opacity: 1;
      transform: translateX(-50%) translateY(0);
    }
  }

  .feedback.success {
    border-color: var(--as-success);
    color: var(--as-success);
  }

  /* Markers container */
  .markers {
    position: fixed;
    top: 0;
    left: 0;
    width: 0;
    height: 0;
    z-index: var(--as-z-markers);
    pointer-events: none;
  }

  /* Individual marker */
  .marker {
    position: absolute;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 24px;
    height: 24px;
    background: var(--as-accent);
    border: 2px solid white;
    border-radius: 50%;
    color: white;
    font-size: var(--as-font-size-xs);
    font-weight: 700;
    box-shadow: var(--as-shadow-md);
    pointer-events: auto;
    cursor: pointer;
    transform: translate(-50%, -50%);
    transition: transform var(--as-transition-fast), box-shadow var(--as-transition-fast);
  }

  .marker:hover {
    transform: translate(-50%, -50%) scale(1.15);
    box-shadow: var(--as-shadow-lg);
  }

  .marker.fixed {
    position: fixed;
  }

  .marker.pending {
    opacity: 0.7;
    animation: marker-pulse 1s ease-in-out infinite;
  }

  @keyframes marker-pulse {
    0%, 100% { transform: translate(-50%, -50%) scale(1); }
    50% { transform: translate(-50%, -50%) scale(1.1); }
  }

  /* Marker animations */
  .marker.entering {
    animation: marker-enter 0.25s ease-out;
  }

  .marker.exiting {
    animation: marker-exit 0.2s ease-in forwards;
  }

  @keyframes marker-enter {
    from {
      opacity: 0;
      transform: translate(-50%, -50%) scale(0);
    }
    to {
      opacity: 1;
      transform: translate(-50%, -50%) scale(1);
    }
  }

  @keyframes marker-exit {
    from {
      opacity: 1;
      transform: translate(-50%, -50%) scale(1);
    }
    to {
      opacity: 0;
      transform: translate(-50%, -50%) scale(0);
    }
  }

  /* Marker tooltip */
  .marker-tooltip {
    position: absolute;
    bottom: calc(100% + 8px);
    left: 50%;
    transform: translateX(-50%);
    padding: var(--as-space-sm) var(--as-space-md);
    background: var(--as-bg-primary);
    border: 1px solid var(--as-border-primary);
    border-radius: var(--as-radius-md);
    box-shadow: var(--as-shadow-md);
    font-size: var(--as-font-size-sm);
    white-space: nowrap;
    max-width: 300px;
    pointer-events: none;
    z-index: var(--as-z-tooltip);
    animation: tooltip-enter 0.15s ease-out;
  }

  .marker-tooltip::after {
    content: '';
    position: absolute;
    top: 100%;
    left: 50%;
    transform: translateX(-50%);
    border: 6px solid transparent;
    border-top-color: var(--as-bg-primary);
  }

  @keyframes tooltip-enter {
    from {
      opacity: 0;
      transform: translateX(-50%) translateY(4px);
    }
    to {
      opacity: 1;
      transform: translateX(-50%) translateY(0);
    }
  }

  .tooltip-element {
    font-weight: 500;
    color: var(--as-text-primary);
    margin-bottom: 2px;
  }

  .tooltip-comment {
    color: var(--as-text-secondary);
    overflow: hidden;
    text-overflow: ellipsis;
  }

  /* Popup - Popover style (positioned near click point) */
  .popup-popover {
    position: fixed;
    z-index: var(--as-z-popup);
    width: 340px;
    padding: var(--as-space-lg);
    background: var(--as-bg-primary);
    border: 1px solid var(--as-border-primary);
    border-radius: var(--as-radius-lg);
    box-shadow: var(--as-shadow-lg);
    animation: popover-enter 0.15s ease-out;
  }

  @keyframes popover-enter {
    from {
      opacity: 0;
      transform: scale(0.95) translateY(-4px);
    }
    to {
      opacity: 1;
      transform: scale(1) translateY(0);
    }
  }

  .popup-popover.shake {
    animation: popup-shake 0.3s ease-out;
  }

  @keyframes popup-shake {
    0%, 100% { transform: translateX(0); }
    25% { transform: translateX(-8px); }
    75% { transform: translateX(8px); }
  }

  .popup-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: var(--as-space-md);
  }

  .popup-element {
    font-weight: 500;
    color: var(--as-text-primary);
    font-size: var(--as-font-size-md);
  }

  .popup-path {
    font-family: var(--as-font-mono);
    font-size: var(--as-font-size-xs);
    color: var(--as-text-muted);
    margin-top: 2px;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  .popup-multiselect-header {
    flex: 1;
    min-width: 0;
  }

  .popup-element-list {
    list-style: none;
    margin: var(--as-space-xs) 0 0 0;
    padding: 0;
    font-size: var(--as-font-size-xs);
    color: var(--as-text-secondary);
    max-height: 80px;
    overflow-y: auto;
  }

  .popup-element-list li {
    padding: 2px 0;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  .popup-close {
    padding: var(--as-space-xs);
    background: transparent;
    border: none;
    border-radius: var(--as-radius-sm);
    color: var(--as-text-muted);
    cursor: pointer;
    transition: background var(--as-transition-fast), color var(--as-transition-fast);
  }

  .popup-close:hover {
    background: var(--as-bg-hover);
    color: var(--as-text-primary);
  }

  .popup-body {
    margin-bottom: var(--as-space-lg);
  }

  .popup-textarea {
    width: 100%;
    min-height: 100px;
    padding: var(--as-space-md);
    background: var(--as-bg-secondary);
    border: 1px solid var(--as-border-primary);
    border-radius: var(--as-radius-md);
    color: var(--as-text-primary);
    font-family: inherit;
    font-size: var(--as-font-size-md);
    line-height: 1.5;
    resize: vertical;
    transition: border-color var(--as-transition-fast);
  }

  .popup-textarea:focus {
    outline: none;
    border-color: var(--as-accent);
  }

  .popup-textarea::placeholder {
    color: var(--as-text-muted);
  }

  .popup-footer {
    display: flex;
    justify-content: flex-end;
    gap: var(--as-space-sm);
  }

  .popup-btn {
    padding: var(--as-space-sm) var(--as-space-lg);
    background: transparent;
    border: 1px solid var(--as-border-primary);
    border-radius: var(--as-radius-md);
    color: var(--as-text-primary);
    font-size: var(--as-font-size-sm);
    font-weight: 500;
    cursor: pointer;
    transition: background var(--as-transition-fast), border-color var(--as-transition-fast);
  }

  .popup-btn:hover {
    background: var(--as-bg-hover);
  }

  .popup-btn.primary {
    background: var(--as-accent);
    border-color: var(--as-accent);
    color: white;
  }

  .popup-btn.primary:hover {
    background: var(--as-accent-hover);
    border-color: var(--as-accent-hover);
  }

  .popup-btn.danger {
    color: var(--as-error);
  }

  .popup-btn.danger:hover {
    background: rgba(255, 59, 48, 0.1);
  }

  /* Hover tooltip (follows cursor) */
  .hover-tooltip {
    position: fixed;
    z-index: var(--as-z-tooltip);
    padding: var(--as-space-sm) var(--as-space-md);
    background: var(--as-bg-primary);
    border: 1px solid var(--as-border-primary);
    border-radius: var(--as-radius-md);
    box-shadow: var(--as-shadow-md);
    font-size: var(--as-font-size-sm);
    max-width: 350px;
    pointer-events: none;
  }

  .hover-element {
    font-weight: 500;
    color: var(--as-text-primary);
    margin-bottom: 2px;
  }

  .hover-path {
    font-family: var(--as-font-mono);
    font-size: var(--as-font-size-xs);
    color: var(--as-text-muted);
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  /* Selection rectangle */
  .selection-rect {
    position: fixed;
    z-index: var(--as-z-overlay);
    border: 2px dashed var(--as-accent);
    background: var(--as-accent-light);
    pointer-events: none;
  }

  /* Highlight overlay */
  .highlight {
    position: fixed;
    z-index: var(--as-z-overlay);
    border: 2px solid var(--as-accent);
    background: var(--as-accent-light);
    pointer-events: none;
    transition: all 0.1s ease-out;
  }

  /* Settings panel */
  .settings-panel {
    position: absolute;
    bottom: calc(100% + var(--as-space-md));
    right: 0;
    width: 280px;
    padding: var(--as-space-md);
    background: var(--as-bg-primary);
    border: 1px solid var(--as-border-primary);
    border-radius: var(--as-radius-lg);
    box-shadow: var(--as-shadow-lg);
    animation: settings-enter 0.2s ease-out;
  }

  @keyframes settings-enter {
    from {
      opacity: 0;
      transform: translateY(10px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  .settings-title {
    font-weight: 600;
    margin-bottom: var(--as-space-md);
    padding-bottom: var(--as-space-sm);
    border-bottom: 1px solid var(--as-border-primary);
  }

  .settings-group {
    margin-bottom: var(--as-space-md);
  }

  .settings-label {
    display: block;
    font-size: var(--as-font-size-sm);
    color: var(--as-text-secondary);
    margin-bottom: var(--as-space-xs);
  }

  .settings-select {
    width: 100%;
    padding: var(--as-space-sm);
    background: var(--as-bg-secondary);
    border: 1px solid var(--as-border-primary);
    border-radius: var(--as-radius-md);
    color: var(--as-text-primary);
    font-size: var(--as-font-size-sm);
    cursor: pointer;
  }

  .settings-select:focus {
    outline: none;
    border-color: var(--as-accent);
  }

  .settings-toggle {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: var(--as-space-sm) 0;
  }

  .settings-toggle-label {
    font-size: var(--as-font-size-sm);
  }

  .settings-switch {
    position: relative;
    width: 40px;
    height: 22px;
    background: var(--as-bg-secondary);
    border: 1px solid var(--as-border-primary);
    border-radius: var(--as-radius-full);
    cursor: pointer;
    transition: background var(--as-transition-fast);
  }

  .settings-switch.active {
    background: var(--as-accent);
    border-color: var(--as-accent);
  }

  .settings-switch::after {
    content: '';
    position: absolute;
    top: 2px;
    left: 2px;
    width: 16px;
    height: 16px;
    background: white;
    border-radius: 50%;
    transition: transform var(--as-transition-fast);
  }

  .settings-switch.active::after {
    transform: translateX(18px);
  }

  /* Color picker */
  .color-picker {
    display: flex;
    gap: var(--as-space-xs);
    flex-wrap: wrap;
  }

  .color-option {
    width: 24px;
    height: 24px;
    border: 2px solid transparent;
    border-radius: 50%;
    cursor: pointer;
    transition: transform var(--as-transition-fast), border-color var(--as-transition-fast);
  }

  .color-option:hover {
    transform: scale(1.15);
  }

  .color-option.active {
    border-color: var(--as-text-primary);
  }

  /* Utility classes */
  .hidden {
    display: none !important;
  }

  .sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
  }

  /* Skip animation for elements that have already animated */
  .no-animate {
    animation: none !important;
  }
`,A={scope:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <circle cx="12" cy="12" r="10"/>
    <circle cx="12" cy="12" r="6"/>
    <circle cx="12" cy="12" r="2"/>
  </svg>`,freeze:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <path d="M12 2v20M2 12h20M4.93 4.93l14.14 14.14M19.07 4.93L4.93 19.07"/>
  </svg>`,unfreeze:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <polygon points="5 3 19 12 5 21 5 3"/>
  </svg>`,eye:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"/>
    <circle cx="12" cy="12" r="3"/>
  </svg>`,eyeOff:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <path d="M17.94 17.94A10.07 10.07 0 0 1 12 20c-7 0-11-8-11-8a18.45 18.45 0 0 1 5.06-5.94M9.9 4.24A9.12 9.12 0 0 1 12 4c7 0 11 8 11 8a18.5 18.5 0 0 1-2.16 3.19m-6.72-1.07a3 3 0 1 1-4.24-4.24"/>
    <line x1="1" y1="1" x2="23" y2="23"/>
  </svg>`,copy:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <rect x="9" y="9" width="13" height="13" rx="2" ry="2"/>
    <path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"/>
  </svg>`,trash:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <polyline points="3 6 5 6 21 6"/>
    <path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"/>
    <line x1="10" y1="11" x2="10" y2="17"/>
    <line x1="14" y1="11" x2="14" y2="17"/>
  </svg>`,sun:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <circle cx="12" cy="12" r="5"/>
    <line x1="12" y1="1" x2="12" y2="3"/>
    <line x1="12" y1="21" x2="12" y2="23"/>
    <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/>
    <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/>
    <line x1="1" y1="12" x2="3" y2="12"/>
    <line x1="21" y1="12" x2="23" y2="12"/>
    <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"/>
    <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"/>
  </svg>`,moon:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/>
  </svg>`,x:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <line x1="18" y1="6" x2="6" y2="18"/>
    <line x1="6" y1="6" x2="18" y2="18"/>
  </svg>`,settings:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <circle cx="12" cy="12" r="3"/>
    <path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"/>
  </svg>`};function gn(t){return`
    <div class="toolbar collapsed" data-annotation-toolbar>
      <button class="toolbar-btn toggle-btn" title="${x("toolbar.activate")}" data-action="toggle">
        ${A.scope}
        ${t>0?`<span class="badge">${t}</span>`:""}
      </button>
    </div>
  `}function bn(t){const{scopeCount:n,isFrozen:e,markersVisible:o,isDarkMode:a,showCopiedFeedback:s,showClearedFeedback:r,showEntranceAnimation:i=!1,settingsPanelHtml:d=""}=t;return`
    <div class="toolbar${i?" entering":""}" data-annotation-toolbar>
      ${s?`<div class="feedback success">${x("toolbar.copiedFeedback")}</div>`:""}
      ${r?`<div class="feedback">${x("toolbar.clearedFeedback")}</div>`:""}
      ${d}

      <button class="toolbar-btn ${e?"active":""}" title="${x(e?"toolbar.unfreeze":"toolbar.freeze")}" data-action="freeze">
        ${e?A.unfreeze:A.freeze}
      </button>

      <button class="toolbar-btn ${o?"active":""}" title="${x(o?"toolbar.hideMarkers":"toolbar.showMarkers")}" data-action="toggle-markers">
        ${o?A.eye:A.eyeOff}
      </button>

      <div class="separator"></div>

      <div class="scope-count">
        ${A.scope}
        <span class="count">${n}</span>
      </div>

      <div class="separator"></div>

      <button class="toolbar-btn" title="${x("toolbar.copyToClipboard")}" data-action="copy" ${n===0?"disabled":""}>
        ${A.copy}
      </button>

      <button class="toolbar-btn" title="${x("toolbar.clearAll")}" data-action="clear" ${n===0?"disabled":""}>
        ${A.trash}
      </button>

      <div class="separator"></div>

      <button class="toolbar-btn" title="${x("toolbar.toggleTheme")}" data-action="theme">
        ${a?A.sun:A.moon}
      </button>

      <button class="toolbar-btn" title="${x("toolbar.settings")}" data-action="settings">
        ${A.settings}
      </button>

      <button class="toolbar-btn" title="${x("toolbar.close")}" data-action="close">
        ${A.x}
      </button>
    </div>
  `}function vn(t,n){const e=t.elementInfo.isFixed,o=t.clickX,a=t.clickY;return e?{x:o,y:a,isFixed:!0}:{x:o,y:a-n,isFixed:!1}}function xn(t){const{scope:n,isHovered:e,isExiting:o,isAnimating:a,scrollY:s,accentColor:r,skipTooltipAnimation:i=!1}=t,d=vn(n,s),h=["marker",d.isFixed?"fixed":"",o?"exiting":"",a?"entering":""].filter(Boolean).join(" "),u=`
    left: ${d.x}px;
    top: ${d.y}px;
    background-color: ${r};
  `;return`
    <div
      class="${h}"
      style="${u}"
      data-annotation-marker
      data-scope-id="${n.id}"
      title="${n.elementInfo.humanReadable}"
    >
      ${n.number}
      ${e?yn(n,i):""}
    </div>
  `}function yn(t,n){const e=t.elementInfo.humanReadable,o=t.comment?t.comment.length>100?t.comment.slice(0,100)+"...":t.comment:x("marker.noComment");return`
    <div class="marker-tooltip${n?" no-animate":""}">
      <div class="tooltip-element">${dt(e)}</div>
      <div class="tooltip-comment">${dt(o)}</div>
    </div>
  `}function ut(t,n,e,o){const a=t.x,s=t.isFixed?t.y:t.y-n,r=`
    left: ${a}px;
    top: ${s}px;
    background-color: ${e};
    opacity: 0.7;
  `;return`
    <div
      class="marker pending${t.isFixed?" fixed":""}"
      style="${r}"
      data-annotation-marker
      data-pending="true"
    >
      ${o}
    </div>
  `}function kn(t){const{scopes:n,hoveredMarkerId:e,exitingMarkers:o,animatingMarkers:a,scrollY:s,accentColor:r,pendingMarker:i,pendingMarkers:d=[],skipTooltipAnimation:h=!1}=t,u=n.map(l=>xn({scope:l,isHovered:l.id===e,isExiting:o.has(l.id),isAnimating:a.has(l.id),scrollY:s,accentColor:r,skipTooltipAnimation:h})).join("");let p="";return d.length>0?p=d.map((l,c)=>ut(l,s,r,n.length+1+c)).join(""):i&&(p=ut(i,s,r,n.length+1)),`<div class="markers">${u}${p}</div>`}function dt(t){const n=document.createElement("div");return n.textContent=t,n.innerHTML}function Sn(t,n){const s=window.innerWidth,r=window.innerHeight;let i=t+12,d=n-220/2;return i+340>s-12&&(i=t-340-12),i<12&&(i=Math.max(12,t-340/2)),i=Math.max(12,Math.min(i,s-340-12)),d<12&&(d=12),d+220>r-12&&(d=r-220-12),{left:`${i}px`,top:`${d}px`}}function wn(t){const{elementInfo:n,existingScope:e,isShaking:o,clickX:a,clickY:s,multiSelectInfos:r=[]}=t;if(!n&&!e)return"";const i=r.length>1,d=(e==null?void 0:e.elementInfo)||n,h=(e==null?void 0:e.comment)||"",u=!!e,p=Sn(a,s);let l;if(i){const c=r.slice(0,5).map(y=>`<li>${O(y.humanReadable)}</li>`).join(""),m=r.length>5?`<li>${x("popup.andMore",{count:r.length-5})}</li>`:"";l=`
      <div class="popup-multiselect-header">
        <div class="popup-element">${x("popup.elementsSelected",{count:r.length})}</div>
        <ul class="popup-element-list">${c}${m}</ul>
      </div>
    `}else l=`
      <div>
        <div class="popup-element">${O(d.humanReadable)}</div>
        <div class="popup-path">${O(d.selectorPath)}</div>
      </div>
    `;return`
    <div class="popup-popover ${o?"shake":""}" style="left: ${p.left}; top: ${p.top};" data-annotation-popup>
      <div class="popup-header">
        ${l}
        <button class="popup-close" data-action="popup-close" title="${x("popup.close")}">
          ${A.x}
        </button>
      </div>

      <div class="popup-body">
        <textarea
          class="popup-textarea"
          placeholder="${x(i?"popup.addFeedbackMulti":"popup.addFeedback")}"
          data-popup-input
          autofocus
        >${O(h)}</textarea>
      </div>

      <div class="popup-footer">
        ${u?`
          <button class="popup-btn danger" data-action="popup-delete">
            ${x("popup.delete")}
          </button>
        `:""}
        <button class="popup-btn" data-action="popup-cancel">
          ${x("popup.cancel")}
        </button>
        <button class="popup-btn primary" data-action="popup-submit">
          ${u?x("popup.save"):i?x("popup.addScopes",{count:r.length}):x("popup.addScope")}
        </button>
      </div>
    </div>
  `}function O(t){const n=document.createElement("div");return n.textContent=t,n.innerHTML}function $n(t,n){let s=t+16,r=n+16;return s+350>window.innerWidth&&(s=t-350-16),r+60>window.innerHeight&&(r=n-60-16),s=Math.max(16,s),r=Math.max(16,r),{left:`${s}px`,top:`${r}px`}}function En(t){const{elementInfo:n,x:e,y:o}=t,a=$n(e,o);return`
    <div class="hover-tooltip" style="left: ${a.left}; top: ${a.top};">
      <div class="hover-element">${ft(n.humanReadable)}</div>
      <div class="hover-path">${ft(n.selectorPath)}</div>
    </div>
  `}function pt(t,n){return t?`
    <div
      class="highlight"
      style="
        left: ${t.left}px;
        top: ${t.top}px;
        width: ${t.width}px;
        height: ${t.height}px;
        border-color: ${n};
        background-color: ${n}20;
      "
    ></div>
  `:""}function An(t,n){return t?`
    <div
      class="selection-rect"
      style="
        left: ${t.x}px;
        top: ${t.y}px;
        width: ${t.width}px;
        height: ${t.height}px;
        border-color: ${n};
        background-color: ${n}20;
      "
    ></div>
  `:""}function ft(t){const n=document.createElement("div");return n.textContent=t,n.innerHTML}const Cn={purple:"#AF52DE",blue:"#3c82f7",cyan:"#5AC8FA",green:"#34C759",yellow:"#FFD60A",orange:"#FF9500",red:"#FF3B30"};function Mn(t){const{settings:n,skipAnimation:e=!1}=t,o=[{value:"compact",label:x("settings.outputLevels.compact")},{value:"standard",label:x("settings.outputLevels.standard")},{value:"detailed",label:x("settings.outputLevels.detailed")},{value:"forensic",label:x("settings.outputLevels.forensic")}],a=Object.entries(Cn).map(([s,r])=>({name:s,translatedName:x(`colors.${s}`),hex:r,active:n.scopeColor===r}));return`
    <div class="settings-panel${e?" no-animate":""}" data-annotation-settings>
      <div class="settings-title">${x("settings.title")}</div>

      <div class="settings-group">
        <label class="settings-label">${x("settings.outputLevel")}</label>
        <select class="settings-select" data-setting="outputLevel">
          ${o.map(s=>`<option value="${s.value}" ${n.outputLevel===s.value?"selected":""}>${s.label}</option>`).join("")}
        </select>
      </div>

      <div class="settings-group">
        <label class="settings-label">${x("settings.markerColor")}</label>
        <div class="color-picker">
          ${a.map(s=>`<button
                  class="color-option ${s.active?"active":""}"
                  style="background: ${s.hex};"
                  data-setting="scopeColor"
                  data-value="${s.hex}"
                  title="${s.translatedName}"
                ></button>`).join("")}
        </div>
      </div>

      <div class="settings-group">
        <div class="settings-toggle">
          <span class="settings-toggle-label">${x("settings.blockInteractions")}</span>
          <button
            class="settings-switch ${n.blockInteractions?"active":""}"
            data-setting="blockInteractions"
            data-value="${!n.blockInteractions}"
            title="${x("settings.blockInteractionsHint")}"
          ></button>
        </div>
      </div>

      <div class="settings-group">
        <div class="settings-toggle">
          <span class="settings-toggle-label">${x("settings.showTooltips")}</span>
          <button
            class="settings-switch ${n.showTooltips?"active":""}"
            data-setting="showTooltips"
            data-value="${!n.showTooltips}"
          ></button>
        </div>
      </div>

      <div class="settings-group">
        <div class="settings-toggle">
          <span class="settings-toggle-label">${x("settings.autoClearAfterCopy")}</span>
          <button
            class="settings-switch ${n.autoClearAfterCopy?"active":""}"
            data-setting="autoClearAfterCopy"
            data-value="${!n.autoClearAfterCopy}"
          ></button>
        </div>
      </div>
    </div>
  `}class In extends HTMLElement{constructor(){super();E(this,"core",null);E(this,"shadow");E(this,"unsubscribe",null);E(this,"styleElement");E(this,"contentElement");E(this,"isComposing",!1);E(this,"popupShaking",!1);E(this,"mouseX",0);E(this,"mouseY",0);E(this,"hoveredMarkerId",null);E(this,"toolbarShownOnce",!1);E(this,"settingsPanelAnimated",!1);E(this,"animatedMarkerTooltipId",null);E(this,"lastRenderedSettings",null);this.shadow=this.attachShadow({mode:"open"}),this.styleElement=document.createElement("style"),this.styleElement.textContent=mn,this.contentElement=document.createElement("div"),this.contentElement.className="annotation-root",this.shadow.appendChild(this.styleElement),this.shadow.appendChild(this.contentElement)}static get observedAttributes(){return["theme","output-level","scope-color","disabled"]}connectedCallback(){this.core=pn({settings:this.getSettingsFromAttributes(),loadPersisted:!0,onScopeCreate:e=>this.dispatchScopeEvent("annotation:scope",{scope:e}),onScopeUpdate:e=>this.dispatchScopeEvent("annotation:update",{scope:e}),onScopeDelete:e=>this.dispatchScopeEvent("annotation:delete",{id:e}),onScopesClear:e=>this.dispatchScopeEvent("annotation:clear",{scopes:e}),onCopy:(e,o)=>this.dispatchScopeEvent("annotation:copy",{content:e,level:o})}),this.unsubscribe=this.core.subscribe(e=>this.render(e)),this.setupEventListeners(),this.render(this.core.store.getState()),this.updateThemeAttribute()}disconnectedCallback(){this.unsubscribe&&(this.unsubscribe(),this.unsubscribe=null),this.core&&(this.core.destroy(),this.core=null)}attributeChangedCallback(e,o,a){if(!(o===a||!this.core))switch(e){case"theme":this.core.updateSettings({theme:a||"auto"}),this.updateThemeAttribute();break;case"output-level":this.core.updateSettings({outputLevel:a||"standard"});break;case"scope-color":this.core.updateSettings({scopeColor:a||"#AF52DE"});break;case"disabled":a!==null&&this.core.deactivate();break}}activate(){var e;(e=this.core)==null||e.activate()}deactivate(){var e;(e=this.core)==null||e.deactivate()}toggle(){var e;(e=this.core)==null||e.toggle()}async copyOutput(e){var o;return((o=this.core)==null?void 0:o.copyOutput(e))??!1}getOutput(e){var o;return((o=this.core)==null?void 0:o.getOutput(e))??""}clearAll(){var e;(e=this.core)==null||e.scopes.clearAllScopes()}getSettingsFromAttributes(){const e={},o=this.getAttribute("theme");(o==="light"||o==="dark"||o==="auto")&&(e.theme=o);const a=this.getAttribute("output-level");(a==="compact"||a==="standard"||a==="detailed"||a==="forensic")&&(e.outputLevel=a);const s=this.getAttribute("scope-color");return s&&(e.scopeColor=s),e}updateThemeAttribute(){if(!this.core)return;const e=this.core.getSettings().theme,o=K(e);this.setAttribute("data-theme",e),e==="auto"&&this.setAttribute("data-resolved-theme",o)}setupEventListeners(){this.shadow.addEventListener("click",this.handleClick.bind(this)),this.shadow.addEventListener("mouseover",this.handleMouseOver.bind(this)),this.shadow.addEventListener("mouseout",this.handleMouseOut.bind(this)),document.addEventListener("mousemove",this.handleMouseMove.bind(this)),this.shadow.addEventListener("keydown",this.handleKeyDown.bind(this)),this.shadow.addEventListener("compositionstart",()=>{this.isComposing=!0}),this.shadow.addEventListener("compositionend",()=>{this.isComposing=!1}),this.shadow.addEventListener("change",this.handleChange.bind(this)),document.addEventListener("click",this.handleDocumentClick.bind(this))}handleDocumentClick(e){if(!this.core||!this.core.store.getState().settingsPanelVisible)return;e.composedPath().some(r=>r===this)||this.core.store.setState({settingsPanelVisible:!1})}handleChange(e){const o=e.target;this.handleSettingChange(o)}handleClick(e){var i,d,h;const o=e.target,a=(i=o.closest("[data-action]"))==null?void 0:i.getAttribute("data-action"),s=(d=o.closest("[data-scope-id]"))==null?void 0:d.getAttribute("data-scope-id");if(!this.core)return;switch(a){case"toggle":this.core.toggle();break;case"close":this.core.deactivate();break;case"freeze":this.core.freeze.toggle();break;case"toggle-markers":{const u=this.core.store.getState();this.core.store.setState({markersVisible:!u.markersVisible});break}case"copy":this.core.copyOutput();break;case"clear":this.core.scopes.clearAllScopes();break;case"theme":{const u=this.core.getSettings().theme,l=K(u)==="dark"?"light":"dark";this.core.updateSettings({theme:l}),this.updateThemeAttribute();break}case"settings":{const u=this.core.store.getState();this.core.store.setState({settingsPanelVisible:!u.settingsPanelVisible});break}case"popup-close":case"popup-cancel":this.core.hidePopup();break;case"popup-submit":this.handlePopupSubmit();break;case"popup-delete":this.handlePopupDelete();break}s&&!a&&this.core.showPopup(s),((h=o.closest("[data-setting]"))==null?void 0:h.getAttribute("data-setting"))&&this.handleSettingChange(o)}handleSettingChange(e){if(!this.core)return;const o=e.closest("[data-setting]");if(!o)return;const a=o.getAttribute("data-setting"),s=o.getAttribute("data-value");switch(a){case"outputLevel":{const r=o;this.core.updateSettings({outputLevel:r.value});break}case"scopeColor":s&&this.core.updateSettings({scopeColor:s});break;case"blockInteractions":this.core.updateSettings({blockInteractions:s==="true"});break;case"showTooltips":this.core.updateSettings({showTooltips:s==="true"});break;case"autoClearAfterCopy":this.core.updateSettings({autoClearAfterCopy:s==="true"});break}}handleMouseOver(e){const a=e.target.closest("[data-scope-id]");a&&(this.hoveredMarkerId=a.getAttribute("data-scope-id"),this.render(this.core.store.getState()))}handleMouseOut(e){e.target.closest("[data-scope-id]")&&(this.hoveredMarkerId=null,this.render(this.core.store.getState()))}handleMouseMove(e){this.mouseX=e.clientX,this.mouseY=e.clientY}handleKeyDown(e){var a;e.target.matches("[data-popup-input]")&&(e.key==="Enter"&&!e.shiftKey&&!this.isComposing&&(e.preventDefault(),this.handlePopupSubmit()),e.key==="Escape"&&(e.preventDefault(),(a=this.core)==null||a.hidePopup()))}handlePopupSubmit(){var s;if(!this.core)return;const e=this.core.store.getState(),o=this.shadow.querySelector("[data-popup-input]"),a=((s=o==null?void 0:o.value)==null?void 0:s.trim())||"";if(e.popupAnnotationId)this.core.scopes.updateScope(e.popupAnnotationId,{comment:a});else if(e.multiSelectElements.length>1)for(let r=0;r<e.multiSelectElements.length;r++){const i=e.multiSelectElements[r],d=e.multiSelectInfos[r],h=i.getBoundingClientRect(),u=h.left+h.width/2,p=h.top+h.height/2,l=d.isFixed,c=u,m=l?p:p+window.scrollY;this.core.scopes.addScope(i,a,{clickX:c,clickY:m,isMultiSelect:!0})}else if(e.hoveredElement&&e.popupElementInfo){const r=e.popupElementInfo.isFixed,i=e.popupClickX,d=r?e.popupClickY:e.popupClickY+window.scrollY;this.core.scopes.addScope(e.hoveredElement,a,{clickX:i,clickY:d})}this.core.hidePopup()}handlePopupDelete(){if(!this.core)return;const e=this.core.store.getState();e.popupAnnotationId&&(this.core.scopes.deleteScope(e.popupAnnotationId),this.core.hidePopup())}dispatchScopeEvent(e,o){this.dispatchEvent(new CustomEvent(e,{detail:o,bubbles:!0,composed:!0}))}render(e){const o=e.settings,a=Array.from(e.scopes.values()).sort((i,d)=>i.number-d.number),s=K(o.theme);if(e.settingsPanelVisible){const i=JSON.stringify({settings:o,settingsPanelVisible:e.settingsPanelVisible,scopeCount:a.length,isFrozen:e.isFrozen,markersVisible:e.markersVisible,theme:s});if(this.lastRenderedSettings===i)return;this.lastRenderedSettings=i}else this.lastRenderedSettings=null;let r="";if(e.toolbarExpanded){const i=!this.toolbarShownOnce;i&&(this.toolbarShownOnce=!0);let d="";if(e.settingsPanelVisible){const h=this.settingsPanelAnimated;d=Mn({settings:o,skipAnimation:h}),this.settingsPanelAnimated=!0}else this.settingsPanelAnimated=!1;r+=bn({scopeCount:a.length,isFrozen:e.isFrozen,markersVisible:e.markersVisible,isDarkMode:s==="dark",showCopiedFeedback:e.showCopiedFeedback,showClearedFeedback:e.showClearedFeedback,showEntranceAnimation:i,settingsPanelHtml:d})}else this.toolbarShownOnce=!1,this.settingsPanelAnimated=!1,r+=gn(a.length);if(e.toolbarExpanded&&e.markersVisible){let i=null,d=[];e.popupVisible&&!e.popupAnnotationId&&(e.multiSelectElements.length>1?d=e.multiSelectElements.map((u,p)=>{var b;const l=u.getBoundingClientRect(),c=l.left+l.width/2,m=l.top+l.height/2,y=((b=e.multiSelectInfos[p])==null?void 0:b.isFixed)||!1;return{x:c,y:y?m:m+window.scrollY,isFixed:y}}):e.pendingMarkerX!==0&&(i={x:e.pendingMarkerX,y:e.pendingMarkerY,isFixed:e.pendingMarkerIsFixed}));const h=this.hoveredMarkerId!==null&&this.hoveredMarkerId===this.animatedMarkerTooltipId;this.hoveredMarkerId!==null?this.animatedMarkerTooltipId=this.hoveredMarkerId:this.animatedMarkerTooltipId=null,r+=kn({scopes:a,hoveredMarkerId:this.hoveredMarkerId,exitingMarkers:e.exitingMarkers,animatingMarkers:e.animatingMarkers,scrollY:e.scrollY,accentColor:o.scopeColor,pendingMarker:i,pendingMarkers:d,skipTooltipAnimation:h})}if(e.popupVisible){const i=e.popupAnnotationId?e.scopes.get(e.popupAnnotationId):null;r+=wn({elementInfo:(i==null?void 0:i.elementInfo)||e.popupElementInfo,existingScope:i||null,isShaking:this.popupShaking,clickX:i?i.clickX:e.popupClickX,clickY:i?i.clickY:e.popupClickY,multiSelectInfos:e.multiSelectInfos})}if(e.toolbarExpanded&&!e.popupVisible&&e.hoveredElementInfo&&o.showTooltips&&(r+=En({elementInfo:e.hoveredElementInfo,x:this.mouseX,y:this.mouseY}),e.hoveredElement)){const i=e.hoveredElement.getBoundingClientRect();r+=pt(i,o.scopeColor)}if(e.isSelecting&&e.selectionRect){const i=en(e.selectionRect);r+=An(i,o.scopeColor);for(const d of e.selectionPreviewElements){const h=d.getBoundingClientRect();r+=pt(h,o.scopeColor)}}if(this.contentElement.innerHTML=r,this.positionToolbar(e),e.popupVisible){const i=this.shadow.querySelector("[data-popup-input]");i==null||i.focus()}}positionToolbar(e){const o=this.shadow.querySelector(".toolbar");if(!o)return;const a=20,{toolbarPosition:s}=e.settings;let r,i;switch(s){case"top-left":r=a,i=a;break;case"top-right":r=window.innerWidth-o.offsetWidth-a,i=a;break;case"bottom-left":r=a,i=window.innerHeight-o.offsetHeight-a;break;case"bottom-right":default:r=window.innerWidth-o.offsetWidth-a,i=window.innerHeight-o.offsetHeight-a;break}(e.toolbarPosition.x!==20||e.toolbarPosition.y!==20)&&(r=e.toolbarPosition.x,i=e.toolbarPosition.y),o.style.left=`${r}px`,o.style.top=`${i}px`}}function Et(t="agent-ui-annotation"){customElements.get(t)||customElements.define(t,In)}Et();Et();const G=document.getElementById("console"),Tn=document.getElementById("activate-btn");function H(t,n=!1){const e=document.createElement("div");e.className="console-line"+(n?" error":""),e.textContent=`[${new Date().toLocaleTimeString()}] ${t}`,G.appendChild(e),G.scrollTop=G.scrollHeight}const X=document.getElementById("annotation");X.addEventListener("annotation:scope",t=>{H(`Scope created: ${t.detail.scope.elementInfo.humanReadable}`)});X.addEventListener("annotation:update",t=>{H(`Scope updated: #${t.detail.scope.number}`)});X.addEventListener("annotation:delete",t=>{H(`Scope deleted: ${t.detail.id}`)});X.addEventListener("annotation:clear",t=>{H(`Cleared ${t.detail.scopes.length} scope(s)`)});X.addEventListener("annotation:copy",t=>{H(`Copied ${t.detail.level} output to clipboard`)});Tn.addEventListener("click",()=>{X.activate(),H("agent-ui-annotation activated")});
