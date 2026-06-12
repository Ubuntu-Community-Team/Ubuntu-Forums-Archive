---
title: "Adobe flash player not working in any browser!"
date: 2018-08-09
forum: Multimedia Software
---

### Post by encinoman2 on 2018-08-09
I have just installed a fresh version of Ubuntu 18.04 and despite my best efforts I cannot get any flash content to work in Firefox, Chromium or Brave. I have enabled multiverse, and have run the standard "sudo apt-get update" and then "[COLOR=#333333][FONT=monospace]sudo apt install browser-plugin-freshplayer-pepperflash"[/FONT][/COLOR]. Also tried "sudo update-pepperflashplugin-nonfree". All seems to be installed fine but after restarting each browser the flash media still don't run. Thoughts?

---

### Post by kc1di on 2018-08-10
Did you install third party restricted packages when you install ubuntu? 
if not do this:```
sudo apt install ubuntu-restricted-extras ubuntu-restricted addons
```

---

### Post by Dennis N on 2018-08-10
> All seems to be installed fine but after restarting each browser the flash media still don't run. Thoughts? 
You also need to set the permissions on a web page to allow flash. 

**Firefox**:
1) install the flash player package. 
2) set the permissions on the web page with the flash content:
    Right click on page, select "View Page Info", select "Permissions", find "run adobe flash" in the item list, and change to "Allow".

Chromium:
1) install the flash player package.
2) set the permissions on the web page with the flash content:
    Click icon on left end of address bar > Site Settings > Flash > change to "Allow"

---

