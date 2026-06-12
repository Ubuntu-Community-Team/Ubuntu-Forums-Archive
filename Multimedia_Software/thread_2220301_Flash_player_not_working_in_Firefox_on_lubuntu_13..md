---
title: "Flash player not working in Firefox on lubuntu 13.10"
date: 2014-04-27
forum: Multimedia Software
---

### Post by adam51 on 2014-04-27
Hello,

i tried to install both flashplugin-installer and adobe-flashplugin and neither is working from me. Only thing working is pepper flash plugin for Chromium but Chromium seems to be running slower than Firefox on my old PC.

Does anyone know what to do?
thanks

---

### Post by fugazi32 on 2014-04-27
Had the same issue, found this: [http://itsfoss.com/fix-flash-player-issue-chromium-in-ubuntu-14-04/]("http://itsfoss.com/fix-flash-player-issue-chromium-in-ubuntu-14-04/")

---

### Post by adam51 on 2014-04-27
Thank you for your advice, like I stated up there in my post - pepper flash player solution from [http://itsfoss.com/fix-flash-player-issue-chromium-in-ubuntu-14-04/](http://itsfoss.com/fix-flash-player-issue-chromium-in-ubuntu-14-04/) works fine but I am trying to make flash work in firefox.

---

### Post by SeijiSensei on 2014-04-27
To install the Adobe Flash Player plugin for Firefox and other browsers, use this
```

sudo apt-get update
sudo apt-get install flashplugin-installer
```

---

### Post by adam51 on 2014-04-27
> **SeijiSensei said:**
> To install the Adobe Flash Player plugin for Firefox and other browsers, use this
```

sudo apt-get update
sudo apt-get install flashplugin-installer
```

I have already done that. [QUOTE=adam51]i tried to install both flashplugin-installer and adobe-flashplugin and neither is working from me[/QUOTE]
Does anyone even read my question?
Maybe it's my poor english skill. :p
Anyway, thanks for the answer

I used sudo apt-get install flashplugin-installer, firefox has Shockwave Flash item enabled in plugins but it still does not work. When I go to [http://helpx.adobe.com/flash-player.html](http://helpx.adobe.com/flash-player.html), it does say I got flash 11.2.202 but I don't see any flash animation and there probably should be some. At least down there in the "Verify flash is installed" section

---

### Post by SeijiSensei on 2014-04-27
Look in Firefox's Tools > Add-ons and make sure the plug-in isn't disabled by default.  That's a long-shot, though.

Maybe there's a problem in your Firefox profile.  First, save your bookmarks using Bookmarks > Show All Bookmarks > Import and Backup > Backup.  Now close Firefox with File > Quit, move $HOME/.mozilla to .mozilla.old, then start Firefox again.  It will create a new profile.  Any better?  If so, restore your bookmarks using the same utility.

If that doesn't work, you can try creating another user and logging in with that identity.  Does Flash work then?

I don't see animations on that Adobe page.  How about YouTube, Hulu, or Crunchyroll?

---

### Post by monkeybrain20122 on 2014-04-28
Do you have a clean profile? Maybe you can test with a different profile. 
Close Firefox. Open the file manager, go to your home. Press ctrl+h or choose show hidden files from the menu. Find the hidden folder .mozilla and rename it something else, like .mozilla-bak. Now start Firefox and see if you are still getting problems. 

To revert to the original profile, close FF, delete .mozilla and rename .mozilla-bak back to .mozilla.

---

### Post by adam51 on 2014-05-01
The profile stuff did not help unfortunately. There is a white space on the place where the animation should be on every site SeijiSensei mentioned and there is no message about not having flash player installed. There is a workaround on Youtube fortunately - I can use HTML5 instead.

---

