---
title: "WEP Wireless Connection Trouble?  EASY FIX"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by Fliplip on 2010-05-29
I have struggled with wireless connections via my VisonNet DSL Modem/wireless router, especially in the Ubuntu 9 and 10 versions.  I literally tried everything; different apps to control the wireless cards, fwcutter, Network-Manager, CLI commands, ndiswrapper, proprietary drivers....and oddly, sometimes they would work but on a re-install, then not.  I've been working on this problem for months with various boxes.  Tonight, I discovered a bug in both 9.10 and 10.04 and I believe it's probably in most other versions.    When you are setting up networking, if you use a PassPhrase like I do, of course you pull down the menu to WEP Passphrase and don't use the WEP Key (HEX string, of course.)  The bug fix is this; if you enter your PassPhrase in the KEY window, it will work just fine.  Since my wireless router is setup for a PassPhrase, I can't tell you whether it's true for KEYS, i.e., that you have to enter a KEY in the PassPhrase window.  But I just fixed my 11 yo boy's Ubuntu 9.10 x86 using that, and my own 10.04 x64 installation entering the PassPhrase in the wrong window.  I could never understand why I kept getting splash screens wanting the PassPhrase when I'd already typed it in numerous times.  At first I thought it was a key storage problem with the Gnome Keyring.  Hope this helps both the users and developers.  I never found any workable solutions on the Internet via Google. Fliplip

---

### Post by Stancel on 2010-05-29
what do you mean by "the KEY window"?

---

