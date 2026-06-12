---
title: "Skype video overlay issue"
date: 2010-08-29
forum: Multimedia Software
---

### Post by Redwid on 2010-08-29
Hi there!

I've strange video problem with Skype when during call I'm starting my video. 
Looks like Skype made a copy of top part of the screen and put it on the bottom ... on the right side of my video.

May be I described not so clearly, this is screenshot for example ...

[[IMG]http://img820.imageshack.us/img820/9445/screenshotza.th.png[/IMG]](http://img820.imageshack.us/i/screenshotza.png/)

I don't have two TVs in my living room as Skype shows me. Bottom part is just a copy of top part.

My PC: Laptop Dell Studio 15, integrated web cam (already tried with usb web cam - the same result) and Ubuntu 10.04 (on oldest were the same bug).

Any ideas, where should I dig? 
Video codecs, webcam drivers or settings for them?

---

### Post by Redwid on 2010-08-31
No clue, anyone?

---

### Post by ZeroLinux on 2010-09-01
It seems everyone has this problem but nobody wants to take it seriously. 
I'd be glad to hear solution (or, at least the direction to solve), because it is a problem for me also.

---

### Post by Linuxforall on 2010-09-01
I am a regular skype user, I don't have this or any other problem but there is an issue with skype, if a call is disconnected, reconnecting it makes the camera in skype dysfunctional, it works in other programs though but you have to reboot the system to make it work in skype.

---

### Post by ZeroLinux on 2010-09-01
I have different hardware with Ubuntu system with Skype at my place and at relatives' home. The picture of video is parted (splitted into two parts when you switch on the opportunity to see yourself)

---

### Post by Redwid on 2010-09-03
Somethimes I have the same copy-part on the top, but in the bottom all the time.

I've also asked the same question on [skype forum]("http://forum.skype.com/index.php?showtopic=692843") ... no answers at all.

---

### Post by s.v.z on 2010-09-03
The same problem for me. I`ve just found this thread while looking for a solution.

---

### Post by Redwid on 2010-09-04
Ok, quick update - looks like this are a compize or ATI drivers issue.

I've started two laptops from Ubuntu live CD 10.04 (Dell Studio 1535 and LG R400) and installed skype. Video for skype works fine on both laptops.

Then check installed Ubuntu 10.04 on Dell Studio 1535. With visual effects enabled: Extra and Normal - still have this issue. But on None - skype doesn't have this issue.

---

### Post by Redwid on 2010-09-04
Switched from free to ATI drivers. No luck, the same result.

---

### Post by ZeroLinux on 2010-09-04
Is it a compize problem?

---

### Post by basily on 2010-10-14
Same problem here, and it does seem to go away when I choose "none" for visual effects. Could it just be compiz? Or maybe a particular component of compiz I wonder.

---

### Post by happyisland on 2010-10-28
Same problem here on a laptop with an ATI card. Pretty annoying. What's up with Skype's linux offering being so buggy?

---

### Post by hermannelson on 2010-12-17
Same problem here. Still no resolve.

I  tried the package from the  Skype  site,  same thing.

I wonder if the Debian package would work?

Herman

---

### Post by xc3RnbFO8P on 2010-12-17
Try this:
> gedit /$HOME/.Skype/(YourUserName)/config.xml 
and look for lines something like:
> <TransferWindow>
<Height>240</Height>
<NoCancelConfirmation>0</NoCancelConfirmation>
<Width>480</Width>
<X>3</X>
<Y>647</Y>
</TransferWindow> 

---

### Post by eatsleepfolk on 2010-12-18
> **Ringi said:**
> Try this:
 
and look for lines something like:

I tried this to no avail. Has no one a solution to this problem yet? This is very irritating considering that I can't get video chat to work properly on Empathy either.

---

### Post by xc3RnbFO8P on 2010-12-18
Sorry, I should have said: If got these lines then delete them and then try to add instead:
> <Video>
<CaptureHeight>480</CaptureHeight>
<CaptureWidth>640</CaptureWidth>
</Video> 
or other video resolution (height 320 width 240)
This is just a idea not a known solution

---

### Post by eatsleepfolk on 2010-12-19
> **Ringi said:**
> Sorry, I should have said: If got these lines then delete them and then try to add instead:

or other video resolution (height 320 width 240)
This is just a idea not a known solution

No luck with this either, unfortunately. :(

However, if you uncheck "Show Myself View" under the blue camera icon in the video call window it will correct the problem. You won't be able to see yourself, but you'll at least have an unobstructed view of the person you're talking to.

---

### Post by xc3RnbFO8P on 2010-12-19
Witch version of Skype do you have?
I allways get my Skype [**[COLOR="Cyan"]here[/COLOR]**]("http://www.skype.com/intl/en/get-skype/on-your-computer/linux/post-download/"), ubuntu 8.10 + 
In Synaptic Package manager remove Skype, mark for complete removal.
In /home/your folder/.skype (hidden folder use ctrl - h to see it) delete the skype folder.
Restart the computer and install the Skype Deb Package.

---

### Post by eatsleepfolk on 2010-12-22
> **Ringi said:**
> Witch version of Skype do you have?
I allways get my Skype [**[COLOR=Cyan]here[/COLOR]**]("http://www.skype.com/intl/en/get-skype/on-your-computer/linux/post-download/"), ubuntu 8.10 + 
In Synaptic Package manager remove Skype, mark for complete removal.
In /home/your folder/.skype (hidden folder use ctrl - h to see it) delete the skype folder.
Restart the computer and install the Skype Deb Package.

I had installed the latest version via the terminal, but did as you said and downloaded from the above link and the problem persists. Skype for ubuntu is glitchy in general, at the present time I can't even get it to sign in for more than 5 minutes without disconnecting.

---

### Post by xc3RnbFO8P on 2010-12-23
> **eatsleepfolk said:**
> I had installed the latest version via the terminal, but did as you said and downloaded from the above link and the problem persists. Skype for ubuntu is glitchy in general, at the present time I can't even get it to sign in for more than 5 minutes without disconnecting.
Its problem with Skype servers at the moment, I couldn't connect yesterday.

Here is some screenshots of
Synaptic Package Manager> Skype> Properties> Dependencies

1 Skype
2. libqtgui4
3. libx11-6

Check conflicts

---

### Post by eatsleepfolk on 2010-12-23
Indeed, connectivity seems to be back to normal this morning.


I attached a screenshot of Skype's dependencies and it says there are conflicts, but to be honest I have no idea what this means.

For the record, I am running version 2.1.0.81-1ubuntu5

---

### Post by xc3RnbFO8P on 2010-12-23
In Synaptic Package Manager, check if you got **nspluginwrapper** installed.

---

### Post by gradinaruvasile on 2010-12-23
For testing, download the static linked version from the dkype site, that has everything needed bundled in a single folder. Launch the skype executable from that folder.

Compiz is more buggy than Skype. I dont use compiz anymore and i have no problems.

You should install fusion-icon and the fusion control panel (ccsm or something). Make the icon start up automatically. If you right-click on it, you will have some very useful functions, the first one isthe launch of the compiz configurator (if it is installed).

In the configurator you should activate the video bypass (meaning that videos are not played through compiz, they are rendered directly.

[http://wiki.compiz.org/Plugins/Video](http://wiki.compiz.org/Plugins/Video)

---

### Post by peskito on 2011-01-20
Hi there,

I have the same issue on my desktop 64bits, 10.10 and last skype.
I have a laptop with about the same specs and it is all ok on it (integrated cam).

Any other advice? :)

---

### Post by peskito on 2011-01-20
Hi there,

I have the same issue on my desktop 64bits, 10.10 and last skype.
I have a laptop with about the same specs and it is all ok on it (integrated cam).

Any other advice? :)

---

### Post by peskito on 2011-01-20
Hi there,

I have the same issue on my desktop 64bits, 10.10 and last skype.
I have a laptop with about the same specs and it is all ok on it (integrated cam).

Any other advice? :)

---

### Post by linuxuserforever on 2011-01-22
> **peskito said:**
> Hi there,

I have the same issue on my desktop 64bits, 10.10 and last skype.
I have a laptop with about the same specs and it is all ok on it (integrated cam).

Any other advice? :)

Its a Cairo-Dock problem. In start up applications change from Cairo-Dock(with OpenGL) to Cairo-Dock(with no OpenGL) The way I did it was I added Cairo-Dock(with no OpenGL) to my panel and opened up properties. I copied and pasted all the fields over to the Cairo-Dock(with OpenGL) properties in the start-up menu. After that all issues with Skype were gone.
I don't know if it's required but I did do a reboot.

I very very rarely use the terminal.

Credit to **[[B]MedievalChips**]("http://www.youtube.com/user/MedievalChips") [/B][http://www.youtube.com/watch?v=QZJjsBFIWIc&feature=related](http://www.youtube.com/watch?v=QZJjsBFIWIc&feature=related)

Hope it works for you all

To mess up a Linux box, you need to work at it;
to mess up a Windows box, you just need to work on it.

---

### Post by Redwid on 2011-03-03
Yesterday I've got update to 2.6.32-29 kernel, may be compiz as well (right now I have Compiz 1:0.8.4-0ubuntu15) and this irritated Skype overlay issue gone.

---

### Post by JRBASTIEN on 2011-05-01
I have the 2.6.35-28 kernel and Compiz 1:0.8.6-0ubuntu92 and the issue is still present. I never had this issue with my previous computer that had an NVIDIA card.  My new computer has an ATI Radeon HD 5570 card.

I'm using the FGLRX proprietary driver that is proposed by Maverick.

And don't get confused by LinuxUserForever response.  This is not a white picture showing instead of my image for my camera but really an overlay of the top part of the image that is aside my own camera image.

Anyone has a fix for this yet?

---

### Post by quackinator on 2011-05-04
I finally found a fix for this video overlay problem. First of all, compiz is not the problem, as I also experienced the problem in xfwm when compositing is enabled. Also, it is not because of Cairo-Dock as LinuxUserForever stated. Cairo-Dock with OpenGL requires compositing, that's why the problem seems to be because of Cairo-Dock. Well, it turns out that it is because of Skype using Xv. Here is a tutorial on how to enable Skype to use X11 instead of Xv.

@JRBASTIEN: I also use the FGLRX driver for my ATI Radeon HD 3650 card. This whole problem seems to stem from ATI's driver. I'm quite confident this solution will work for you. Bypassing Xv should get rid of this overlay issue.

[http://forum.skype.com/index.php?showtopic=328901](http://forum.skype.com/index.php?showtopic=328901)

I hope this helps.

---

### Post by JRBASTIEN on 2011-05-05
Thanks for the tip quackinator.  The code compiles fine without any error but I only get a black window when I test my camera after installing this hack.

I forgot to mention that my camera is a Logitech Quickcam and I had to use the preload command to get it working with Skype:  bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

After installing the change to use X11 instead of XV, I tried with and without the preload command and no success.  My camera test was always black.

I remove the change and everything is back to normal (including that strange overlay).

---

### Post by Redwid on 2011-07-04
Suddenly after one update - Skype video started working for me without that issue than I've installed restricted drivers from ATI ('cos youtube playback was too baggy). And this issue popped up again. Removing ATI drivers doesn't resolved it. Then I've installed Ubuntu 11.04, Skype worked out of the box without a problem, that after installing ATI drivers I've got again this Skype overlay issue. And again removing that restricted drivers didn't help me. 

Finally I've made clean installation, and using open drivers. No Skype video issue, youtube video playback (1080p) works fine, overall system performance is good.

Could somebody digs into this to find exact problem?

---

### Post by Les_W on 2011-08-28
I guess you've all found the answer to this by now, but just in case..... I had the same problem and solved it by removing Compiz.

---

