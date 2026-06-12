---
title: "ATI - fglrx vs open source?"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by Merritt.kr on 2007-06-09
Can someone explain to me the difference between FGLRX and... I guess the open source drivers? for ATI cards. From what I can gather, FGLRX are the closed source ATI drivers... I didn't even know they provided us with any!

I am running an ATI x1400... I couldn't even get X to load without downloading and installing fglrx. However now I am having problems with jerky screensaver and video. And glxgears only nets me around 2,000 FPS. Now I am wondering... Can I even USE the open source drivers? Are they better? Am I stuck with fglrx, and this crappy performance? Can I hope for improvements soon?

Thanks for any insights or advice! :)

---

### Post by Perfex on 2007-06-09
This might interest you    [http://www.phoronix.com/scan.php?page=article&item=735&num=1]("http://www.phoronix.com/scan.php?page=article&item=735&num=1")

---

### Post by Alex Fernandez on 2007-06-09
fglrx has better performance, over the mesa open source drivers - but they also have more issues heh

---

### Post by Merritt.kr on 2007-06-09
That was interesting Perfex. Thanks.

Seems as though it's mostly a waiting game... for ATI to catch up and make my card work properly, huh? Ah well... I still love Linux. I've only booted into Windows once in two weeks, and wow does it ever feel clunky and ugly. I've tweaked linux so much it's nice and smooth and just how I like it. ;) Hopefully ATI will get out some good drivers for me and the rest of us ATI users soon! A lot of people seem to be having issues with the x1400.

---

### Post by Kubunteando on 2007-06-09
Check [http://ati.amd.com](http://ati.amd.com) for driver updates, and also for installation guidelines and troubleshooting. They have very good information.

The Open Source drivers a really good for a bit older cards unsupported alredy by ATI like the Radeon 9000. But for new cards like yours the ATI proprietary drivers are the best choice.

---

### Post by Merritt.kr on 2007-06-10
Well, fglrxinfo gives me this:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8)

So, I assume that 8.34.8 is my driver version. The newest version listed on the ATI site is 8.37.6

So, the question becomes: Should I upgrade it? Could this cause a problem? And how should I go about it? And why does the package manager not automatically update it?
Thanks!..

---

### Post by Kubunteando on 2007-06-10
I checked the Release Notes of the new 8.37.6 and it is mentioned in the known issues:

Video tearing during playback. Further details can be found in topic number 737-26984

I tried to find some more details using the topic number (search in ATI page) but the knowledgebase did not open the link...
You can try to find some more info on this.

Unfortunately ATI is known for releasing crappy drivers for Linux.
I have made my decision of buying an Nvidia card next time.

I guess you have to decide to upgrade or not, check the forums around, if someone with your same card had troubles using the new drivers.

Usually is not automatically upgraded by the package manager because Ubuntu only supports the ATI drivers that are known to "work" with most cards. And because you never know how the new ATI drivers will behave with your card...

Is the same story as always, you loose lot of time while installing the appropriate graphic drivers on ATI...

---

### Post by Merritt.kr on 2007-06-10
All right, thank you for that. I am looking up issues with the new driver for my card.

Another question: I found out there is apparently a version of the Catalyst Control Center for Linux. Is this a GOOD thing to have, or should I ignore it? I found it pretty useful under windows. And for the life of me I cannot find a download for the linux version! lol they definitely don't like to make it easy for us over at ATI.

---

### Post by Merritt.kr on 2007-06-10
Alright, I found the fglrx-control in Synaptic. Suddenly I have a cute, if undevelopped control center in the KMenu. I'm still not sure about updating my driver, some people claim a number of problems. Is there a way to roll back to the old driver, if the new one screws things up?

---

### Post by Kubunteando on 2007-06-11
Yes, you can always go back and install the previous driver.

If the graphical environment does not start, edit the file /etc/X11/xorg.conf and replace "fglrx" with "radeon".
An reboot the computer, that way you can start the graphical environment again to install the previous driver.

Then you can set back the file xorg.cong to the previous one by replacing the "radeon" by "fglrx" and reboot the computer.

---

### Post by eye208 on 2007-06-11
> **Merritt.kr said:**
> However now I am having problems with jerky screensaver and video. And glxgears only nets me around 2,000 FPS.
**Jerky video:**
Be sure to enable Xvideo. Enter "sudo aticonfig --ovt Xv" into a terminal, then restart X.

**Crappy 3D performance:**
Be sure to disable composite mode. Add the following lines to your xorg.conf file:
```
Section "Extensions"
    Option "NoComposite"
EndSection
```

ATI Mobility chipsets have a feature called PowerPlay which can be used to underclock the card. You can get a list of available modes by entering "aticonfig --lsp" (no sudo required) and set a particular mode by entering "aticonfig --set-powerstate=<number>" (again, no sudo required).

Check these out before installing a newer version of fglrx.

---

### Post by Merritt.kr on 2007-06-11
I'm afraid I haven't had alot of success editing files in consoles. I'm sure it's fairly easy, I just can't figure out the commands to add and edit lines, and save the file to get back to normal console lines...

Thanks for the info by the way :)

---

### Post by eye208 on 2007-06-11
If I remember correctly, there is a shortcut in the Konqueror context menu "Edit as root". Otherwise run "kdesu kate <filename>" in a terminal.

---

### Post by Merritt.kr on 2007-06-11
eye208: I did both of those, however upon restart X would not load. I signed into my account and tried "startx" and got a bunch of lines, the most important seeming to be this:

(EE) NoComposite is not a valid value for the extension option problem when converting the config data structures
(EE) Error parsing the config file

I'm assuming there is a way to edit this from the base console outside of X, but I just don't know how. If I can set it back to "false" as it was before, it'd hopefully load X...


EDIT: Nevermind. Found out that nano can edit from base console outside of X. Used the help file to find out that apparently ^ means Ctrl. :???: I changed it back to "false" and X loaded. I did "sudo aticonfig --ovt Xv" and still get jerky video occasionally - I am seriously starting to think it is firefox taking up resources... Still very low FPS.

---

### Post by Merritt.kr on 2007-06-12
Curious.... could my attempts to make Beryl work have caused this dreadfully low fps?

[http://forum.notebookreview.com/showthread.php?t=126423](http://forum.notebookreview.com/showthread.php?t=126423)

---

### Post by eye208 on 2007-06-12
> **Merritt.kr said:**
> (EE) NoComposite is not a valid value for the extension option
Please be careful when editing configuration files. The error message says you were using "NoComposite" as a value for an "Extension" option. This is not what I pasted here. "Extensions" is the name of the **section**, "NoComposite" is the **option**. It works without a value.

---

### Post by Merritt.kr on 2007-06-12
Okay well a few things...
I upgraded to the newest fglrx driver without issue.

About the NoComposite, I guess I wasn't paying enough attention, it looked too much like the composite option I went through to get Beryl working a while ago. I changed it to what you specified, and X loaded fine.

glxgears gives me this:

kristen@Merritt:~$ glxgears
6434 frames in 5.0 seconds = 1285.102 FPS
6800 frames in 5.0 seconds = 1359.839 FPS
7186 frames in 5.0 seconds = 1437.188 FPS
6988 frames in 5.0 seconds = 1397.437 FPS
7280 frames in 5.0 seconds = 1455.845 FPS
7362 frames in 5.0 seconds = 1472.165 FPS

actually lower than I was getting before, for some reason.


aticonfig --lsp
gives me:

    core/mem      [flags]
-----------------
  1: 209/135 MHz  [low voltage]
  2: 392/252 MHz
* 3: 432/396 MHz  [default state]

I am assuming it means it is set to max.


"sudo aticonfig --ovt Xv" did not fix jerky video.

Any other ideas?

---

### Post by Merritt.kr on 2007-06-12
Also something I have noticed... Kubuntu seems to run my processors at half speed sometimes, even when plugged in. Sometimes at the full 1.6 Ghz, sometimes down to 800 Mhz... I can't really see any reason why it changes this, and it really should be running at full speed when plugged in, since it's not trying to conserve power... is there somewhere I can set these functions?

*****Never mind. I found the control, just right clicking the battery icon in sys tray... no change to fps or jerky video with it running at full speed however.

---

### Post by Merritt.kr on 2007-06-12
With the new driver came a new version of the linux Catalyst Control Center, which includes a section on 3D...

Is it possible changing something in here would fix my FPS issues?

---

