---
title: "Downloading files hosted on the rtmp:// protocol"
date: 2007-09-29
forum: Multimedia &amp; Video
---

### Post by elreteipos on 2007-09-29
Is it possible to download files off of the rtmp:// protocol?

---

### Post by Corey on 2007-11-13
I haven't found out how to do this yet either, save for a few shareware windows apps. I'll be watchin this thread though, hope someone comes up with a  solution.

---

### Post by elreteipos on 2007-11-14
Actually, I found a solution to my problem a while ago. I just forgot about this topic.

Check this out:
[http://www.orbitdownloader.com/](http://www.orbitdownloader.com/)

It's a Windows application, but it's free and works flawlessly thanks to the efforts of the Wine project. I use it at least three times a week.

---

### Post by Corey on 2007-11-14
Thank you Thank you Thank you! You're my new internet hero.

---

### Post by v4169sgr on 2007-12-21
The BBC iPlayer site works off the RTMP protocol.

So I just installed wine from the repos [i32 Dapper], and installed Orbit as above. Installs flawlessly, comes up great, but I have a problem between the keyboard and chain in actually understanding how to use it to download BBC iPlayer content.

Can anyone advise?

---

### Post by elreteipos on 2007-12-22
I'm afraid I can't give you any concrete advise as I'm from outside the UK. I can however explain what I did to download some other rtmp:// stuff myself.

Before explaining how to track down these URLs, you should know that Orbit integrates with Firefox on Windows flawlessly. It'll install some add-on that sniffs your pages for rtmp:// content or something.

If you don't want to switch to Windows every time you want to download something, here's something you could try on Ubuntu. First, open up Adblock Plus (a Firefox add-on) for a list of everything that is embedded on the video page. Look for something that could be a playlist. In my case, this entry looked interesting:

[[img]http://img101.imageshack.us/img101/6060/ccsiteul4.th.jpg[/img]](http://img101.imageshack.us/img101/6060/ccsiteul4.jpg)

Once you've found the correct entry, right-click it and click Copy. Then paste the URL in your address bar. You should see something like this:

[[img]http://img101.imageshack.us/img101/2415/ccsite1su4.th.jpg[/img]](http://img101.imageshack.us/img101/2415/ccsite1su4.jpg)

And there you have it. Note that this technique doesn't work with every site, but it's worth trying if you want to stay away from Windows.

---

### Post by v4169sgr on 2007-12-22
Thanks. I have adblock, and looked at the iPlayer site. There were several javascripts referenced, but I could not see any reference to a downloadable link. The big cheese seems to be a SWF object.

Do you think that installing IE or Firefox in wine would help?

---

### Post by elreteipos on 2007-12-23
So I installed Flash, Firefox and the most recent version of Orbit Downloader. Long story short: the [sniffer](http://img508.imageshack.us/img508/6151/grabbergx6.jpg) doesn't detect the video. I think that's because the Orbit Downloader plugin/addon (not sure) failed to install properly. Feel free to mess around with it yourself though.

You can find the plugin in */Program Files/Orbit Downloader/addons* and the addon in */media/WINDOWS XP/Program Files/Orbit Downloader/addons/orbitff*. The Firefox profile directory can be found in */home/pdedecker/.wine/drive_c/windows/profiles/*USERNAME*/Application Data/Mozilla/Firefox/Profiles*. Let us know if you can find a way to do it. :) (You might have to install Orbit Downloader on Windows and copy the extension to Firefox's profile directory on Wine.)

One more thing: here's how to use the grabber.
- [http://www.orbitdownloader.com/Use-as-RTMP-Downloader.htm](http://www.orbitdownloader.com/Use-as-RTMP-Downloader.htm)

---

### Post by v4169sgr on 2007-12-23
I'm looking at this:

[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

Any comments?

---

