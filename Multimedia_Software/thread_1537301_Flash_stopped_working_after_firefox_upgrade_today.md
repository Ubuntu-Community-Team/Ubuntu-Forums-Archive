---
title: "Flash stopped working after firefox upgrade today"
date: 2010-07-23
forum: Multimedia Software
---

### Post by linas on 2010-07-23
Hi,

Ran a routine apt-get upgrade yesterday, which pulled in firefox 3.6.7 (for Jaunty 9.04).  After restarting firefox, youtube stopped working.

-- Before the upgrade, I was regularly watching youtube, without a problem, using the non-free Adobe flash player.

-- After the upgrade, firefox started using swfdec 0.8.2 instead of flashplayer, even though the firefox applications dialog called for flashplayer -- its as if firefox was ignoring preferences. Since swfdec is not yet capable of playing youtube videos, this is clearly bad

-- I apt-get removed the swfdec-mozilla player, restarted firefox, and now get only a black rectangle where the video should be.

The firefox plugins dialog shows that the adobe flash plugin is installed & enabled (version 10.1.53 -- the latest, as installed via apt-get install flashplugin-installer); the firefox applications dialog shows adobe flash as the application to use for swf's. 

This was all working just fine 2 days ago, and all broke with the firefox upgrade.

All I want is the ability to watch youtube; don't care what brand of player it takes to do this. Suggestions?  Google seems to know nothing about this...

---

### Post by lovinglinux on 2010-07-23
Looks like some Hardy and Jaunty installations have problems with Flash 10.1 in Firefox. I tested it without success, although I have seen some users reporting that it works.

Are you using 64bit or 32bit?

Until we can figure out a solution to your problem, you can get YouTube to work using my extension FlashVideoReplacer.

[http://flvideoreplacer-extension.blogspot.com](http://flvideoreplacer-extension.blogspot.com)
[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

---

### Post by lovinglinux on 2010-07-23
I still need to test Jaunty, but so far Hardy, Karmic and Lucid are working fine with Firefox 3.6.7 and flash from the repositories.

Try version 1.0.9 of my extension [FLASH-AID]("http://flash-aid-extension.blogspot.com").

---

### Post by linas on 2010-07-23
Wild guess: seems to have something to do with javascript not properly interacting with plugins ??? 

I visited [http://www.adobe.com/support/flash/ts/documents/java_script_comm/javascript_to_flash.html](http://www.adobe.com/support/flash/ts/documents/java_script_comm/javascript_to_flash.html)

and I don't see any flash window/box/display, and typing in text into the text entry box doesn't do anything.

Next, I explored FlashVideoReplacer -- still no luck. I saw that gecko-mediaplayer was prefered, so I installed that first. Then installed FlashVideoReplacer 1.01 (since 1.0.2 is still in a sandbox & I don't have a mozilla login).  Restart the browser, and, when visiting youtube, I now see "gxine browser plugin" in a black rectangle, the video URL at the top of the rectangle and nothing else, nothing plays.  I have both gxine and gxineplugin installed from before.

The lack of responsiveness makes me think that neither plugin is seeing the mouse/mousclicks, and/or are failing to respond to some javscript communications channel between plugin and browser.

---

### Post by linas on 2010-07-23
BTW, am using 32-bit Jaunty. 

Installed flash-aid-1.0.9rc (with flashvideoreplacer still active) and still get a non-responsive black rectangle with the text "gxine browser plugin" in it.

Then disabled flashvideoreplacer; this now returns the system to a non-responsive black rectangle with no text.

---

### Post by no2498 on 2010-07-23
try using  opera  till they get firefox fixed

---

### Post by lovinglinux on 2010-07-23
> **linas said:**
> BTW, am using 32-bit Jaunty. 

Installed flash-aid-1.0.9rc (with flashvideoreplacer still active) and still get a non-responsive black rectangle with the text "gxine browser plugin" in it.

Then disabled flashvideoreplacer; this now returns the system to a non-responsive black rectangle with no text.

First, get FLASH-AID 1.0.9 instead of the 1.0.9rc. There is no difference between the two, but if you have a version from the Beta Channel you will receive only updates from that channel (ie, betas and release candidates). There is no need to run it again tho.

Then enable FlashVideoReplacer, visit [this page]("http://www.youtube.com/watch?v=u7deClndzQw&feature=related") and check if the plugin loads properly. If you still see a rectangle with gxine plugin text, then click it. If it doesn't work, then disable gxine to let gecko-mediaplayer take over.

---

### Post by Cavsfan on 2010-07-23
Try the Java links in my sig. One is to test the version and the other has instructions on how to update it.
On that 2nd page the 32 bit instructions are on the left.

EDIT: the update page is writen for JRE 6 update 20.
You will need to change the 20 to 21 wherever necessary.

---

### Post by HellHornet on 2010-07-23
I have got the same problem on Karmic Kuala, but its slightly different since youtube actually works even while giving an error that flash has crashed, its just that some of the other flash based sites that I use dont load. serves me right for not reading what the update was about. I have installed the flash aid and flash replacer, but still got the same problem. Chrome also gives the same problem.

---

### Post by HellHornet on 2010-07-23
Awesome got it working again, disabled flash replacement and just let flash aid re-download a fresh flash copy and voila flash is back. Thanks guys

---

### Post by Cavsfan on 2010-07-23
> **HellHornet said:**
> Awesome got it working again, disabled flash replacement and just let flash aid re-download a fresh flash copy and voila flash is back. Thanks guys

That's good! Mine didn't stop working with the FF update. **lovinglinux** is good with the flash stuff!
I am no authority on Java, but the 2 sites in my sig work well. It'd be worth checking to see if you have 6.20 or 21.

Hopefully linas will get his working.

---

### Post by michael.white on 2010-07-23
> **lovinglinux said:**
> First, get FLASH-AID 1.0.9 instead of the 1.0.9rc. There is no difference between the two, but if you have a version from the Beta Channel you will receive only updates from that channel (ie, betas and release candidates). There is no need to run it again tho.

Then enable FlashVideoReplacer, visit [this page]("http://www.youtube.com/watch?v=u7deClndzQw&feature=related") and check if the plugin loads properly. If you still see a rectangle with gxine plugin text, then click it. If it doesn't work, then disable gxine to let gecko-mediaplayer take over.

All I wanted to do this evening was relax and watch some videos.  But no - the last upgrade (pushed on 7/23/10 to x86_64 9.10) killed my 64-bit flash plugin, normally running under x86_64 Firefox.  I even installed Opera and the flash plugin died there, too.  As a side note, I don't understand why people like Opera - that horrible "speed dial", that clunky manual cookie acceptance interface, the ways it tries to "help" me type in a web page.

My keyboard needed reconstruction after this annoyance.  Thanks to flashaid for fixing the problem.  Anyway, that is the LAST upgrade I ever take automatically.  From now on, it's pick and choose as needed.  I guess I should have learned my from girlfriend's experience when an upgrade wiped out her Japanese language support.

---

### Post by michael.white on 2010-07-23
> **lovinglinux said:**
> Looks like some Hardy and Jaunty installations have problems with Flash 10.1 in Firefox. I tested it without success, although I have seen some users reporting that it works.

Are you using 64bit or 32bit?

Until we can figure out a solution to your problem, you can get YouTube to work using my extension FlashVideoReplacer.

[http://flvideoreplacer-extension.blogspot.com](http://flvideoreplacer-extension.blogspot.com)
[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

FlashVideoReplacer won't install on my machine (x86_64 9.10, x86_64 Firefox 3.6.7, AMD FX51).  I go to [https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

-------------------------------
Firefox could not install the file at 

[https://addons.mozilla.org/en-US/firefox/downloads/latest/161869/addon-161869-latest.xpi?src=addondetail](https://addons.mozilla.org/en-US/firefox/downloads/latest/161869/addon-161869-latest.xpi?src=addondetail)

because: Invalid file hash (possible download corruption)
-261
-----------------------------------

I tried several times.  I know, not directly related to the original posting......

---

### Post by linas on 2010-07-23
Hmm, now I'm getting two different behaviors:

1) many/most youtube videos display a message at top of black rectangle: 

   You need to upgrade your Adobe Flash Player to watch this video.
   Download it from Adobe.

Given that I have Adobe completely disabled at this point, I was surprised to see this recommendation. But it seems that youtube embeds this string in the page, and the javascript somehow decides to display it.

2) Some videos e.g. those embedded in 

[http://singularityhub.com/2010/07/23/new-zealands-robot-legs-let-paraplegics-walk-for-150000-video/](http://singularityhub.com/2010/07/23/new-zealands-robot-legs-let-paraplegics-walk-for-150000-video/)

are showing rectangle with light/dark gray diagonal bars, and a message:
"The plugin for this content has been disabled. Click here to manage your plugins" 
As I have absolutely no clue what the mime type for the content is, this is a rather totally useless suggestion. Arghhh. (well, I'm pretty sure its something streamed from youtube, but no idea what that is.)

3) re gxine suggestion above: when I said "non-responsive" I meant it: clicking, left, right, middle does nothing to start gxine or bring up any gxine menus/dialogues. Disabling gxine just causes #1) above (i.e. gecko-mediaplayer is not invoked)

4) The reason I installed 1.09rc instead of 1.09 is because 1.09 is "sandboxed" and cannot be installed without creating a login with Mozilla foundation.  Given that I have maybe 50+ different logins on 50+ websites, I really don't want to create yet another one.

---

### Post by linas on 2010-07-23
> **Cavsfan said:**
> Try the Java links in my sig. One is to test the version and the other has instructions on how to update it.

Sorry, what's Java got to do with it? I've got Java disabled in the browser, by default, and have not enabled it in a decade ...

---

### Post by lovinglinux on 2010-07-24
> **michael.white said:**
> All I wanted to do this evening was relax and watch some videos.  But no - the last upgrade (pushed on 7/23/10 to x86_64 9.10) killed my 64-bit flash plugin...Thanks to flashaid for fixing the problem...

Adobe killed the 64bit plugin and the available version has a critical vulnerability, so you are better now.

> **michael.white said:**
> FlashVideoReplacer won't install on my machine (x86_64 9.10, x86_64 Firefox 3.6.7, AMD FX51)....

Go to the [extension home page]("http://flvideoreplacer-extension.blogspot.com"). Look for the Stable Channel in the sidebar. Instead of clicking the *Automatic Install* option, click the *Download* option. It will download the file from Google Code server instead of Mozilla. When the download is completed, go to Firefox menu, click "File >> Open File" and select the downloaded xpi file. It will install automatically. Restart Firefox.

> **linas said:**
> Hmm, now I'm getting two different behaviors:

1) many/most youtube videos display a message at top of black rectangle: 

2) Some videos e.g. those embedded in 



Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

> **linas said:**
> 
3) re gxine suggestion above: when I said "non-responsive" I meant it: clicking, left, right, middle does nothing to start gxine or bring up any gxine menus/dialogues. Disabling gxine just causes #1) above (i.e. gecko-mediaplayer is not invoked)

The gxine plugin is preventing gecko-mediaplayer from being invoked. That's a common problem when you install multiple plugins.

To solve that run the command below, restart Firefox then try again.

```
sudo apt-get remove gxineplugin
```


> **linas said:**
> 4) The reason I installed 1.09rc instead of 1.09 is because 1.09 is "sandboxed" and cannot be installed without creating a login with Mozilla foundation.  Given that I have maybe 50+ different logins on 50+ websites, I really don't want to create yet another one.

I know. What I was trying to say is that in the Stable Channel you will find two links : *Download* and *Automatic Install*. The second requires an account because that version is still sandboxed, the first gets the file from Google Code server. No account needed, but you need to open it with Firefox to install.

---

### Post by KirbySmith on 2010-07-24
Ah!  This may be the goldmine thread I was looking for last night before it existed.  My short-form commiseration is "me too."  In my case, however, messing around trying to get Crunchyroll and news sites to work has led to having two flashplayers installed: 10.1.r53 and the previous 9.0.r999.  And Crunchyroll eventually worked for no apparent reason, but doesn't now after a reboot.  Another unwanted diversion attempting to fix it has been unsuccessful.

Anyway...

First, I don't know how to kill one or the other of the flash players beyond the disable mode in the Add-on menu.

Second, I'm unclear whether I should kill one or the other before trying some of the advice in this thread.

Direction is welcome

Thanks

kirby

32-bit Ubuntu 9.10

---

### Post by KirbySmith on 2010-07-24
FLASH-AID seems to have helped, but I don't have time to test the result fully right now.  It cleaned out version 9 of Flashplayer (YAY!) and Crunchyroll video now runs, at the moment at least.

Note: After downloading the FLASH-AID .xpi file, I used Firefox/file/open on the file. 

I clicked on the FLASH-AID icon in the lower right of the Firefox window and clicked install to initiate the process.

Thanks lovinlinux

kirby

---

### Post by lovinglinux on 2010-07-24
@linas

The problem with gxine is that YouTube changed the code on  their pages, so I need to update the extension. It is not working for me either.

> **KirbySmith said:**
> FLASH-AID seems to have helped, but I don't have time to test the result fully right now.  It cleaned out version 9 of Flashplayer (YAY!) and Crunchyroll video now runs, at the moment at least.

Note: After downloading the FLASH-AID .xpi file, I used Firefox/file/open on the file. 

I clicked on the FLASH-AID icon in the lower right of the Firefox window and clicked install to initiate the process.

Thanks lovinlinux

kirby

You are welcome.

---

### Post by shivugh on 2010-07-24
**Here's how I solved the flash problem with firefox:**:D

After I updated firefox to 3.6.7, the flash based videos stopped working and interestingly audio only in youtube. 

First I removed all types of flash plugins from /usr/lib using the terminal (sudo rm /usr/lib/mozilla...........)

Checked about:plugins in firefox and interestingly flash version 9 still remained undeleted (coz the file is hidden in .mozilla folder) and therefore removed that too.

Then I downloaded and installed latest flash version 10 from the adobe website directly.

Restarted firefox and it now works like a charm.

---

### Post by shivugh on 2010-07-24
Damn smiley, it is **about: plugins** without space.

---

### Post by lovinglinux on 2010-07-24
Anyone experiencing issues with FlashVideoReplacer, please get version 1.0.3 from the extension blog or from Mozilla sandbox.

[http://flvideoreplacer-extension.blogspot.com](http://flvideoreplacer-extension.blogspot.com)
[https://addons.mozilla.org/en-US/firefox/addon/161869/versions/](https://addons.mozilla.org/en-US/firefox/addon/161869/versions/)

This version fixes changes introduced on YouTube on July 22nd, which prevented videos from loading.

---

### Post by bfrederi on 2010-08-01
Flash-Aid is a nice resource that does simple things, but is extremely helpful. I did nearly every step that Flash-Aid does, except I forgot to remove the plugin in /usr/lib/mozilla. I like how it shows every step that it performs, so I could see where I went wrong. Thanks!

---

### Post by lovinglinux on 2010-08-01
> **bfrederi said:**
> Flash-Aid is a nice resource that does simple things, but is extremely helpful. I did nearly every step that Flash-Aid does, except I forgot to remove the plugin in /usr/lib/mozilla. I like how it shows every step that it performs, so I could see where I went wrong. Thanks!

You are welcome.

---

### Post by michael.the.bone on 2010-08-06
I'm still unable to get youtube working.

I followed all the steps from last time when flash wasn't working, so i have made the path true etc...

I have flash aid and flash video replacer, but nothing is working, the video box is there and it loads up, but i can't press play.

Also, it say's that i dont have flash player if i try to play anything off myspace and when i have tried to download a flash packed it suggests (both open and save as), it hasn't run...

Please help, i have the last episode of twin peaks to watch!

Cheers

---

### Post by PhotonicGuy on 2010-08-06
I stopped using Firefox. Before I let it make only major upgrades. In this way I think i was able avoid such bugs and incompatibilities

---

### Post by sir4taye on 2010-09-03
Flash-aid fixed my flash. 

Appearantly, 64bit flash is to unsafe and disabled at the moment. It installed the 32-bit version right away and you tube works beautifully now. 

Thanks much.

---

### Post by lovinglinux on 2010-09-03
> **sir4taye said:**
> Flash-aid fixed my flash. 

Appearantly, 64bit flash is to unsafe and disabled at the moment. It installed the 32-bit version right away and you tube works beautifully now. 

Thanks much.

You are welcome.

---

