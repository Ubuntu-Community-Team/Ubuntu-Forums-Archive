---
title: "Need flash upgrade to use cool music web page-please help"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by OsakaWilson on 2008-01-02
Can someone tell me how to get [this web page]("http://www.thesixtyone.com/") working in Firefox. When you you try to play music on the page, it gives this message:

Linux users: If music is not playing, you need to upgrade to adobe flash 9r115. (You're probably using 9r48).

Which is very cool of them, but I don't know how to go about upgrading. A search for the keywords "flash 9r115 upgrade" got no hits.

Any ideas?

---

### Post by NilsE on 2008-01-02
0.0.115 is the current version supported by Ubuntu but as far as I know there is still a problem with the one in the repositories. 

Download the following deb file and open it with gdebi or install it with apt and let it install even though it tells you there is one in the repo. Make sure FF is shut down when you install.

[http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

---

### Post by famous3warriors on 2008-01-02
In firefox do about:plugins and take a snap shot picture so I could see what you have going on in firefox.  I took a look at the site and it worked great for me.

---

### Post by OsakaWilson on 2008-01-02
I got a "wrong architecture" message when opening the .deb. I failed to mention that I'm using 64bit Gutsy.

Is there a similar .deb for 64bit?

---

### Post by OsakaWilson on 2008-01-02
Nils,
I can call up the page with about:plugins, but what do you mean by snapshot? Does the flash info below that I took from the about:plugins page help? 

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by sammando on 2008-01-02
Check out this post for installing flash on 64-bit ubuntu

[http://ubuntuforums.org/showpost.php?p=2863873&postcount=1](http://ubuntuforums.org/showpost.php?p=2863873&postcount=1)

If you have problems with that script, you can also try copying the libflashplayer.so file (after downloading and extracting the flash 9 tarball from adobe) into your mozilla plugins directory.

- sam (from thesixtyone)

---

### Post by NilsE on 2008-01-02
> **OsakaWilson said:**
> Nils,
I can call up the page with about:plugins, but what do you mean by snapshot? Does the flash info below that I took from the about:plugins page help? 

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Take Screenshot under accessories is a way to take a snapshot of the screen and/or active window.

That info you provided confirmed you are on the older version of flash.

The deb for the 64bit version is in the first post of this thread.

[http://ubuntuforums.org/showthread.php?t=636397&highlight=flashplugin](http://ubuntuforums.org/showthread.php?t=636397&highlight=flashplugin)

Here is a direct link to the deb file.

[http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466](http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466)

---

### Post by OsakaWilson on 2008-01-02
That did it. Thanks a lot.

---

### Post by OsakaWilson on 2008-01-02
Sammando,

I appreciate that thesixtyone put the note to Linux users on the front page. I probably would have just not returned to the site after it didn't work the first time, but now I've been listening to new bands all morning (it's been morning in Japan) and I'll be a regular at the site.

---

