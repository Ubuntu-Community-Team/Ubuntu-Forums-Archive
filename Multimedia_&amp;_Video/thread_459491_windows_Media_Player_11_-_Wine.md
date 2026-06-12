---
title: "windows Media Player 11 - Wine"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by mpgarate on 2007-05-30
on the wine app page for wmp 11, there are a few posts hinting that it was possible to get around the windows gunuine checker. Has anyone had success with this? I took a stab with little luck

wine app page for wmp11, with comments: [http://appdb.winehq.org/appview.php?iVersionId=4919](http://appdb.winehq.org/appview.php?iVersionId=4919)

---

### Post by steevols on 2007-05-30
Try this link: [No-WGA WMP11]("http://rapidshare.com/files/26503856/WMP11-WindowsXP-x86-DEU-noWGA.zip.html") 24.9 MB

---

### Post by mpgarate on 2007-05-30
I downloaded that and opened it with wine.. lucky guessed the accept buttons (its in german), it ran some scripts, gave an error (in german, a google translation made no sense) and whenever I try to run it again, error immediately.


edit: running the file in the terminal returns this:
```

mike@mike-desktop:~/Desktop/WMP11-WindowsXP-x86-DEU-noWGA.zip_FILES$ wine WMP11-WindowsXP-x86-DEU-noWGA.exe 
fixme:shell:SHAutoComplete SHAutoComplete stub
fixme:exec:SHELL_execute flags ignored: 0x00000580
fixme:advapi:RegisterEventSourceW ((null),L"PDH"): stub
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ole:CoGetClassObject class {acadf079-cbcd-4032-83f2-fa47c4db096f} not registered
err:ole:CoGetClassObject no class object {acadf079-cbcd-4032-83f2-fa47c4db096f} could be created for context 0x1
fixme:wintrust:WinVerifyTrust 0xffffffff {fc451c16-ac75-11d1-b4b8-00c04fb66ea0} 0x7cd39f04
fixme:wintrust:WTHelperProvDataFromStateData (nil)
fixme:wintrust:WinVerifyTrust 0xffffffff {fc451c16-ac75-11d1-b4b8-00c04fb66ea0} 0x7cd39f04
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {cfc399af-d876-11d0-9c10-00c04fc99c8e} could be created for context 0x1
err:seh:setup_exception stack overflow 52 bytes in thread 000e eip 7ec04aec esp 00240fcc stack 0x241000-0x340000
```

---

### Post by steevols on 2007-05-30
I haven't tried it myself; I just saw it on the WINE page.

---

### Post by mpgarate on 2007-06-01
has anyone had success with this?

---

### Post by Chriss.Hi on 2007-06-01
download the dlls listed here [http://appdb.winehq.org/appview.php?iVersionId=4919](http://appdb.winehq.org/appview.php?iVersionId=4919)
> pdh.dll, odbcbcp.dll and gdiplus.dll

---

### Post by mpgarate on 2007-06-02
I believe I did that correctly... in the /windows/system32 directory? Im gonna retry now...

---

### Post by mpgarate on 2007-06-02
no success

---

### Post by khughitt on 2007-06-09
anyone have luck with 10?

---

### Post by mpgarate on 2007-06-09
i havent tried ten... the whole reason I wanted 11 was to use URGE. I have a subscription and love it, but its the only thing tying me down to windows (I still go back to our old crappy xp machine, when I have this beautiful dell amd dual core bought without windows)

---

### Post by khughitt on 2007-06-09
What is urge? Another thing you can do at least until something compatible is available on Linux is to install windows on VMware or Virtualbox.. that way at least you can run in from inside Ubuntu without having to reboot.

---

### Post by mpgarate on 2007-06-09
yea... but I dont have a legal copy of windows and I dont want to break the law. I bought this computer with no os from dell, then ubunu'd it


urge is a subscription music store

---

### Post by ethana2 on 2008-01-18
I'm subscribing to this thread.  I must have my playback speed changer...
Classical music just doesn't cut until you crank it to 1.4x tempo.. sometimes even more...
...oh, and I tried getting that feature with amarok and exaile...

'No sorry, this feature would be out of focus for Amarok. It's really not a DJ application.'
(no response from exail, but they haven't even caught up with amarok yet, so...)

Windows Media Player in WINE is my only hope then, I guess.  That feature has been in WMP since 9, right?  Does 9 work?

---

### Post by ethana2 on 2008-01-18
Not to bash them too much but really - why do you give your project a motto that's outside it's own scope?

Amarok- Fast Forward
...oh wait, you can't!
Rediscover your music!
...and listen to it at the tempo it was /meant/ to be heard!  1x!

---

### Post by timseal on 2008-02-06
mplayer has the audio pitch altering feature you're talking about (if I understand you correctly).  Not the version in Gutsy though.  You can get a newer build from smplayer.sf.net - btw smplayer is a frontend to mplayer, and it's excellent.

-tim

---

### Post by ethana2 on 2008-02-06
Tim, thank you very, very much.  I shall try this.  You have given me hope :)

---

### Post by ethana2 on 2008-02-06
SMPlayer doesn't seem to normalize the pitch while altering the tempo..
I'll see if I can submit a feature request or something..

---

### Post by rvm4000 on 2008-02-06
SMPlayer also has an option to normalize the volume. I've just tried both options and it seems to work ok.

If you enabled the normalization option in preferences, be sure it's also activated in the menu audio -> filters, as the setting in preferences applys to new files, but not already played ones.

---

### Post by ethana2 on 2008-02-06
You're confusing volume and pitch.

I'm talking about playing music at 1.6x sans chipmunks.

---

### Post by ethana2 on 2008-02-06
Hey wait!  I think I found that option!  ...now it plays nothing.

---

### Post by ethana2 on 2008-02-06
Hey, I got it!  Time to cancel that feature request..  Sweeeet.  Thanks, tim.

---

### Post by ethana2 on 2008-02-06
Well, it can't find the plugin or whatever to preserve pitch when i run it from the terminal, but between 1 and 2x, the shift is less than an octave anyway, so I think i can live with it.

That'll probably get fixed soon anyway.  I eagerly await the next release.

---

### Post by rvm4000 on 2008-02-06
To run from a terminal:

mplayer **-af scaletempo** (rest of options)

If you also want the normalization filter:

mplayer **-af scaletempo,volnorm** (rest of options)

By the way, both filters accept options for fine-tune. See the [MPlayer manpage](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html).

---

### Post by oDDWare on 2008-02-19
> **mpgarate said:**
> I believe I did that correctly... in the /windows/system32 directory? Im gonna retry now...

Did you register them? 
oDDWare@oDDWare:~$ regsvr32 "C:\windows\system32\the .dll file"
You probably did, I'm very new, and just suggesting what I can think of.

---

