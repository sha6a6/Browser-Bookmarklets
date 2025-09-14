# Browser Bookmarklets

A collection of useful JavaScript bookmarklets that enhance your web browsing experience with one-click functionality. These lightweight tools work across all modern browsers without requiring any extensions or installations.

## 🚀 What are Bookmarklets?

Bookmarklets are small JavaScript programs stored as browser bookmarks. When clicked, they run on the current webpage to add new functionality. Think of them as tiny browser extensions that don't need installation!

## ✨ Features

- 🎥 **YouTube Tools**: Copy video URLs with timestamps, manage Watch Later playlist
- ⚡ **Lightweight**: Pure JavaScript, no dependencies or installations needed
- 🌐 **Universal**: Works on Firefox, Chrome, Safari, Edge, and other modern browsers
- 🚀 **Instant**: One-click functionality without page reloads
- 🔒 **Privacy-focused**: No data collection, runs entirely in your browser

## 📚 How to Install Bookmarklets

### For Beginners - Step by Step Guide

**Method 1: Using Bookmarks Bar (Recommended)**
1. **Show your bookmarks bar** (if hidden):
   - **Chrome/Edge**: Press `Ctrl+Shift+B` (Windows) or `Cmd+Shift+B` (Mac)
   - **Firefox**: Press `Ctrl+Shift+B` or go to View → Toolbars → Bookmarks Toolbar
   - **Safari**: Press `Cmd+Shift+B` or View → Show Bookmarks Bar

2. **Add the bookmarklet**:
   - Right-click on your bookmarks bar
   - Select "Add bookmark" or "New bookmark"
   - **Name**: Give it a short name (like "YT Copy Time")
   - **URL/Location**: Copy and paste the JavaScript code from below
   - Click "Save"

3. **Use it**: Navigate to the target website and click your new bookmark!

**Method 2: Using Bookmark Manager**
1. Press `Ctrl+Shift+O` (Windows) or `Cmd+Shift+O` (Mac) to open bookmark manager
2. Click "Add new bookmark" or the "+" button
3. Fill in name and paste the JavaScript code as URL
4. Save and use!

---

## 🎥 YouTube Bookmarklets

### Copy Video with Timestamp
Instantly copy the current YouTube video URL with the exact playback time - perfect for sharing specific moments!

**📋 Copy this code:**
```javascript
javascript:(function(){var v=document.querySelector('video');if(v){var t=Math.floor(v.currentTime);var url=window.location.href.split('&t=')[0].split('#t=')[0]+(window.location.href.indexOf('?')>-1?'&':'?')+'t='+t+'s';navigator.clipboard.writeText(url);alert('Copied: '+url);}else{alert('No video found');}})();
```

**How to use:**
1. Go to any YouTube video
2. Play the video and pause at your desired moment
3. Click the bookmarklet
4. The timestamped URL is now copied to your clipboard!

**Example output:** `https://youtube.com/watch?v=VIDEO_ID&t=123s`

📁 [View source code](https://github.com/sha6a6/Browser-Bookmarklets/blob/main/bookmarklets/youtube-copy-timestamp.js)

---

### Remove from Watch Later
Quickly remove the current video from your YouTube Watch Later playlist without navigating through menus.

**📋 Copy this code:**
```javascript
javascript:(function(){var saveBtn=document.querySelector('button[aria-label*="Save"]:not([aria-label*="Download"]), #top-level-buttons button[aria-label*="Save"]:not([aria-label*="Download"])');if(saveBtn&&saveBtn.offsetParent!==null){saveBtn.click();setTimeout(function(){var watchLaterOptions=document.querySelectorAll('ytd-playlist-add-to-option-renderer');var found=false;for(var i=0;i<watchLaterOptions.length;i++){var option=watchLaterOptions[i];var text=option.textContent||option.innerText;if(text.includes('Watch later')){var checkbox=option.querySelector('tp-yt-paper-checkbox');var isChecked=checkbox&&(checkbox.hasAttribute('checked')||checkbox.getAttribute('aria-checked')==='true'||option.hasAttribute('selected'));if(isChecked){checkbox.click();found=true;setTimeout(function(){document.dispatchEvent(new KeyboardEvent('keydown',{key:'Escape',keyCode:27,which:27}));},1200);break;}}}if(!found){document.dispatchEvent(new KeyboardEvent('keydown',{key:'Escape',keyCode:27,which:27}));}},1000);}else{var menu=document.querySelector('#menu button[aria-label="More actions"], #top-row #menu button[aria-label="More actions"]');if(menu){menu.click();setTimeout(function(){var saveInMenu=document.querySelectorAll('tp-yt-paper-listbox ytd-menu-service-item-renderer, ytd-menu-popup-renderer ytd-menu-service-item-renderer');var saveFound=false;for(var i=0;i<saveInMenu.length;i++){var menuText=saveInMenu[i].textContent||saveInMenu[i].innerText;if(menuText.includes('Save')&&!menuText.includes('Download')){saveInMenu[i].click();saveFound=true;setTimeout(function(){var watchLaterOptions=document.querySelectorAll('ytd-playlist-add-to-option-renderer');var found=false;for(var j=0;j<watchLaterOptions.length;j++){var option=watchLaterOptions[j];var text=option.textContent||option.innerText;if(text.includes('Watch later')){var checkbox=option.querySelector('tp-yt-paper-checkbox');var isChecked=checkbox&&(checkbox.hasAttribute('checked')||checkbox.getAttribute('aria-checked')==='true'||option.hasAttribute('selected'));if(isChecked){checkbox.click();found=true;setTimeout(function(){document.dispatchEvent(new KeyboardEvent('keydown',{key:'Escape',keyCode:27,which:27}));},1200);break;}}}if(!found){document.dispatchEvent(new KeyboardEvent('keydown',{key:'Escape',keyCode:27,which:27}));}},1000);break;}}if(!saveFound){document.dispatchEvent(new KeyboardEvent('keydown',{key:'Escape',keyCode:27,which:27}));}},800);}}})();
```

**How to use:**
1. Go to any YouTube video that's in your Watch Later playlist
2. Click the bookmarklet
3. The video is silently removed from Watch Later (no popup notifications!)

**Note:** Only works on videos that are currently in your Watch Later playlist.

📁 [View source code](https://github.com/sha6a6/Browser-Bookmarklets/blob/main/bookmarklets/youtube-remove-watch-later.js)

---

## 🔧 Troubleshooting

**Bookmarklet not working?**
- Make sure you copied the **entire** JavaScript code including `javascript:` at the beginning
- Try refreshing the webpage and clicking again
- Check that you're on the correct website (e.g., YouTube for YouTube bookmarklets)
- Some browsers block bookmarklets on certain pages - try a different page

**No bookmarks bar visible?**
- **Chrome**: Go to Settings → Appearance → Show bookmarks bar
- **Firefox**: Right-click near the address bar → Bookmarks Toolbar
- **Safari**: View → Show Bookmarks Bar

## 🤝 Contributing

Found a bug? Have a cool bookmarklet idea? Contributions are welcome!

1. Fork this repository
2. Create a new branch for your feature
3. Add your bookmarklet to the appropriate folder
4. Update this README with installation instructions
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⭐ Found this helpful?

If these bookmarklets saved you time, consider giving this repo a star! It helps others discover these useful tools.

---

*Made with ❤️ for the web community*
