# 🚀 Extracting Endpoints from JavaScript using a Bookmarklet

## 📌 Overview
This bookmarklet allows security researchers and bug bounty hunters to quickly extract hidden API endpoints from JavaScript files loaded on a webpage. It's a simple yet powerful tool to aid in reconnaissance.

## 🔧 How to Use
1. **Create a new bookmark** in your browser.
2. **Edit the bookmark** and replace the URL with the following JavaScript code:

```javascript
javascript:(function(){var scripts=document.getElementsByTagName("script"),regex=/(?<=(\"|\'|\`))\/[a-zA-Z0–9_?&=\/\-\#\.]*?(?=(\"|\'|\`))/g;const results=new Set;for(var i=0;i<scripts.length;i++){var t=scripts[i].src;""!=t&&fetch(t).then(function(t){return t.text()}).then(function(t){var e=t.matchAll(regex);for(let r of e)results.add(r[0])}).catch(function(t){console.log("An error occurred: ",t)})}var pageContent=document.documentElement.outerHTML,matches=pageContent.matchAll(regex);for(const match of matches)results.add(match[0]);function writeResults(){results.forEach(function(t){document.write(t+"<br>")})}setTimeout(writeResults,3e3);})();
```

3. **Visit any target website** and click the bookmark.
4. The extracted endpoints will be displayed directly on the page.

## 🎯 Why Use This?
✅ **Quick & Easy** – No need for external tools. Just a browser bookmark!  
✅ **Effective Recon** – Find hidden API endpoints that could lead to vulnerabilities.  
✅ **Bug Bounty Friendly** – Enhance your testing workflow and increase findings.  

## 🛠 Example Usage
1. Navigate to any website you are testing.
2. Click on the bookmarklet.
3. View extracted API endpoints in real-time.

## 💡 Contributing
Feel free to contribute by improving the script, suggesting new features, or reporting issues.

## 📢 Support & Share
If you found this useful, don't forget to star ⭐ the repo and share it with fellow security researchers! 🚀

---
#CyberSecurity #BugBounty #PenTesting #Infosec #Reconnaissance #BugBountyTools #EthicalHacking #WebSecurity #SecurityResearch
