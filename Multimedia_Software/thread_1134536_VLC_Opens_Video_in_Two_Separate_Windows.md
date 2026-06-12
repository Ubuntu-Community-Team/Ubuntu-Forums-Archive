---
title: "VLC Opens Video in Two Separate Windows"
date: 2009-04-23
forum: Multimedia Software
---

### Post by feature on 2009-04-23
Hopefully this is the right area, but since I upgraded to Jaunty (I did a full reformat, not an actual "upgrade") whenever I open a video with VLC it opens in two windows (the controls in one window and the video in a separate window). I'd like to change this behaviour to open all in one single window. I have already enabled the "One instance when started from file" and the "Allow only one running instance" options, but still it does the same.

I am running the final release of Jaunty x86 on an Intel Core2Duo, and it is VLC 0.9.9a (from the standard repositories)

I know its not really an Ubuntu issue, but it is my 2nd to last annoyance since the upgrade, I'm just fishing for some advice.

Thanks to all the devs who worked on this, I am very happy :D

---

### Post by orkinoks on 2009-04-23
This is a known bug which was already discussed in the forum.It is told that this bug does not exist version 1.0.0, but it is still a beta.

---

### Post by feature on 2009-04-23
sweet, thats all i needed to hear

my other annoyance (crackling audio) was resolved by turning off pulse audio and using alsa audio instead

/me does a happy dance

---

### Post by Greg Xix on 2009-04-24
I IMMEDIATELY went hunting for and eventually learned to install a Pre-Release version of VLC 1.0.0 and it appears they have fixed this issue. I decided I wasnt going to adapt to the current version(0.9.9) after I couldnt fix it.

Here is a link to the PPA I used for that VLC v1.0.0. If you or anybody else viewing this Thread need help installing it, I will post step by step instructions for you. As I was pulling my hair out for a few hours until I learned out how easy this PPA is (Took about 3 minutes). :)

[https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)


I too like to do fresh & clean installs of my OS's, especially this time around because I installed a new Video Card in my machine a few weeks ago.

I have been a loyal fan of VLC for almost 3 years now, first using it on XP, Vista and now Ubuntu as my "Swiss Army Knife Media Player". So I am feeling a bit relieved now.

---

### Post by gummybear on 2009-04-24
> **Greg Xix said:**
> If you or anybody else viewing this Thread need help installing it, I will post step by step instructions for you. As I was pulling my hair out for a few hours until I learned out how easy this PPA is (Took about 3 minutes). :)

I would gladly appreciate that step by step tutorial.  Also wanting to fix this separate windows problem.  Thanks in advanced.

---

### Post by Greg Xix on 2009-04-24
Okay for the person(s) who needed a Layman's guide to installing VLC pre-release 1.0.0. There are a lot of steps but they are easy, and I was trying to break it down remedially. But I am not trying to be condescending.

Also make sure you have the current crummy version 0.9.9 uninstalled before proceeding.

_Here is what I did:_


1. In Ubuntu goto: System > Administration > Software Sources

2. On the top select the Third Party Software tab

3. Click this weblink: [https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)

4. Near the top-left corner (or from here copy):

*deb [http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) jaunty main*

5. Back in Third Party Software click add

6. Paste that copied line into the field box and press Add Source

**IMPORTANT!! Make sure that you copy the WHOLE ENTIRE line and not just the glowing URL portion**

7. Copy the second line from the webpage:

*deb-src [http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) jaunty main*

8. Repeat steps 5 & 6 for this one as well

9. Minimize but DON'T CLOSE everything; Now go to your Desktop

10. Right-click on anywhere on your desktop and select: Create Document > Empty File and name it something you will remember, like KEYFILE.

11. Open the KEYFILE


12. Back on the webpage click the highlighted portion of: 

*This repository is signed with  1024R/2F021AC1*

13. On this new webpage click on the higlighted portion of: 1024R/2F021AC1

Now you see a whole bunch of "Hieroglyphics"

14. Copy everything that is NOT at the top of the page, bold, and oversized. In other words, copy **ONLY** this:

[B]-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXgCHAEEALIft85AjPrpngbLA+zRPiMBT/gEO2Dr/wkABeRcx/AQLVEAE4te7VMVAlJ0
nUVHNuL9955evX+0vuL4iqeUUBh7Ufan3BRPv0ryzLtDAZYfxb4F0Jya/XoMgYA6mxNFshvt
gg9EDrvNVEqIhfI0BeBBqy45k/NKa31Qnu8C0OU1ABEBAAG0FUxhdW5jaHBhZCBQUEEgZm9y
IEtvd4i2BBMBAgAgBQJJeAIcAhsDBgsJCAcDAgQVAggDBBYCAwECHgECF4AACgkQDklNuy8C
GsEAWQP/QTthVWFM+7AhMY7r8mkMEXmbnRR97boIL8glQX5QKzKHpcCvd6kOqVcYsBz6eAMr
yBjRosVw4f01q9pvqvoAqX3UVgCBaaNG+N0uK5JmKAK+4c6fWGrm1ODZitvKdN60AnkazDaU
excHeV6AtNQrUMpQeHpYcAnnWHjMV4Ybolc=
=bmqW
-----END PGP PUBLIC KEY BLOCK-----[/B]


15. Paste this into your KEYFILE on the desktop. Save & Close. You can also close that weird looking webpage as well.

16. Back in Software Sources, select the Authentication tab

17. Select Import Key File

18. Now browse the KEYFILE you made on the desktop and select OK.

There should now be a third Item there stating something like "Launchpad PPA for Kow"

19. Click Close, and when a new box pops up, click Reload and wait for Ubuntu to do its thing and it will close automatically.

20. Now go back to Add/Remove Applications and try re-adding VLC. You can now delete the KEYFILE as well.

You should now have a "pre-release" version of VLC 1.0.0

Test it out with an AVI file or DVD. Also you can select Help and About and it should say something like:  1.0.0-pre1 Goldeneye

I noticed the video's in Fullscreen mode tend to "chop" when I move my mouse while its playing the movie. But its a Alpha/Beta version of VLC and are still working the bugs. But I can happily live with it because that lousy Separated screen is gone!!

---

### Post by ashmew2 on 2009-04-25
Thanks for the pointers Greg Xix ,  i was pretty much irritated by the two separate window thing ..But i guess ill wait a little bit longer so the 1.x.x is more stable ;)

---

### Post by abhiroopb on 2009-04-26
This is really useful, I installed the 1.0 version and its great. BUT I am having a problem with the video.

The video freezes whenever I play any video in VLC or smplayer and with a variety of video and video formats.

This did not happen in intrepid. Any thoughts? Anything I should try or check?

This applies also even if the video is not in full screen. It just hangs at random points. The video freezes for a brief period (the audio continues fine) and then the video starts up again. This is highly irritating! Does not have anything to do with compiz, as if I disable compiz, it still freezes.

Again this happens in both Smplayer (here it freezes completely, and doesn't even restart) and in VLC (where it freezes and restarts).

I feel like tearing my hair out. Its almost completely impossible to watch videos now.

---

### Post by victorgreen on 2009-04-26
thanks a lot i cant stand two seperate windows so annoying

---

### Post by tanha on 2009-04-26
Is there a workaround for this bug without having to upgrade? 

Also, aside from "integrate video in interface" not working when selected, has anyone else noticed "show a controller in fullscreen" does not work when selected as well? Is there a possible workaround for that too?

---

### Post by lerougegorge on 2009-04-26
Am also noticing VLC problems in 9.04. Playing a video makes my screen go very, very dim (brightness is turned down) - any suggestions on how to fix this?

---

### Post by tanha on 2009-04-27
OK... well, if I do upgrade, can I always downgrade to the current version of vlc if I want to do so?

thanks in advance...

---

### Post by Arup on 2009-04-27
> **tanha said:**
> OK... well, if I do upgrade, can I always downgrade to the current version of vlc if I want to do so?

thanks in advance...

Yes you can, remove the repository line and then remove vlc and reinstall it.

---

### Post by tanha on 2009-04-27
> **Arup said:**
> Yes you can, remove the repository line and then remove vlc and reinstall it.

cool, thanks.

---

### Post by Greg Xix on 2009-04-28
> **lerougegorge said:**
> Am also noticing VLC problems in 9.04. Playing a video makes my screen go very, very dim (brightness is turned down) - any suggestions on how to fix this?




> **abhiroopb said:**
> This is really useful, I installed the 1.0 version and its great. BUT I am having a problem with the video.

The video freezes whenever I play any video in VLC or smplayer and with a variety of video and video formats.

This did not happen in intrepid. Any thoughts? Anything I should try or check?

This applies also even if the video is not in full screen. It just hangs at random points. The video freezes for a brief period (the audio continues fine) and then the video starts up again. This is highly irritating! Does not have anything to do with compiz, as if I disable compiz, it still freezes.

Again this happens in both Smplayer (here it freezes completely, and doesn't even restart) and in VLC (where it freezes and restarts).

I feel like tearing my hair out. Its almost completely impossible to watch videos now.



I honestly dont know for either of your questions. Personally, if I had the time, I would reinstall Ubuntu from scratch(i.e. re-download the ISO and re-burn it slowest speed possible). I took the hour to back everything up and do a fresh install rather than use that glorified update from within 8.10, dont know if you did that or not for 9.04 originally.


One thing to check: cables. Last month I partially knocked out my VGA cable from the back of my screen, it was only slighly, but it made my videos flicker really bad, but no screen colors were affected. So I was dumbfounded until I saw it.

Ubuntu is more fun, but a pain as well.

---

### Post by abhiroopb on 2009-04-28
> **Greg Xix said:**
> I honestly dont know for either of your questions. Personally, if I had the time, I would reinstall Ubuntu from scratch(i.e. re-download the ISO and re-burn it slowest speed possible). I took the hour to back everything up and do a fresh install rather than use that glorified update from within 8.10, dont know if you did that or not for 9.04 originally.


One thing to check: cables. Last month I partially knocked out my VGA cable from the back of my screen, it was only slighly, but it made my videos flicker really bad, but no screen colors were affected. So I was dumbfounded until I saw it.

Ubuntu is more fun, but a pain as well.


1. Might be the cable, but I can always see it (as its a laptop).

2. I did a clean install and this happened immediately, so i doubt re-installing would do anything to help.

Thanks for the help

---

### Post by Greg Xix on 2009-04-28
> **abhiroopb said:**
> 1. Might be the cable, but I can always see it (as its a laptop).

2. I did a clean install and this happened immediately, so i doubt re-installing would do anything to help.

Thanks for the help


Dang. I would try reinstalling 8.10 again and see if the problem persists. Sounds like your laptop and 9.04 dont like eachother. I assume that you have the current NVIDIA drivers on there?

I now figure you dont use any cable since you do have a laptop.

---

### Post by reesje on 2009-04-28
> **Greg Xix said:**
> Dang. I would try reinstalling 8.10 again and see if the problem persists. Sounds like your laptop and 9.04 dont like eachother. I assume that you have the current NVIDIA drivers on there?

I now figure you dont use any cable since you do have a laptop.
I have almost the same laptop (DV5248ea), and it looks like I have the same problem with videofreezes. 

I know from earlier releases of ubuntu that the Geforce Go 7400 is not too good in linux. I have never been able to use compiz and do video playback at the same time without tearing (not a lot, but visible though).

BR,
René

---

### Post by Greg Xix on 2009-04-29
To the 2 laptop users with the Video problem. I just noticed the same thing on my Laptop. 

I just installed Jaunty on there and Youtube will play fine in the default size but if I make it "Fullscreen" it has that freezing problem as well.

If I get some spare time I will report this issue as a bug.

I hope that otherwise the users with the split windows in VLC have been able to upgrade. I have noticed no issues with the pre-release 1.0.0 other than the minor flicker, but thats only with mouse movement while playing.

---

### Post by Arup on 2009-04-29
> **Greg Xix said:**
> To the 2 laptop users with the Video problem. I just noticed the same thing on my Laptop. 

I just installed Jaunty on there and Youtube will play fine in the default size but if I make it "Fullscreen" it has that freezing problem as well.

If I get some spare time I will report this issue as a bug.

I hope that otherwise the users with the split windows in VLC have been able to upgrade. I have noticed no issues with the pre-release 1.0.0 other than the minor flicker, but thats only with mouse movement while playing.

Do you know what video chip your laptop uses? It purely looks like a video driver issue to me.

---

### Post by Nat90 on 2009-04-29
Hi, I'm using Kubuntu 9.04, I tried following Greg Xix's instruccion, but when it comes to importing the key File to the sources, adept(KDE's Synaptic) doesn't recognize it. The default filter is "PGP Keys"; should I name the file with an extension?

Thanks for the help

Edit:

When I went back to re-install the older version, the new one was there, I didn't even have to import the key file.
Thanks!

BTW, does anyone know how to get the play/stop etc menu in full screen mode?

---

### Post by ubername on 2009-04-30
Thanks Greg, your step by step guide worked well.

---

### Post by johnnylavah on 2009-04-30
> **Greg Xix said:**
> Okay for the person(s) who needed a Layman's guide to installing VLC pre-release 1.0.0. There are a lot of steps but they are easy, and I was trying to break it down remedially. But I am not trying to be condescending.

Also make sure you have the current crummy version 0.9.9 uninstalled before proceeding.

_Here is what I did:_


1. In Ubuntu goto: System > Administration > Software Sources

2. On the top select the Third Party Software tab

3. Click this weblink: [https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)

4. Near the top-left corner (or from here copy):

*deb [http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) jaunty main*

5. Back in Third Party Software click add

6. Paste that copied line into the field box and press Add Source

**IMPORTANT!! Make sure that you copy the WHOLE ENTIRE line and not just the glowing URL portion**

7. Copy the second line from the webpage:

*deb-src [http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) jaunty main*

8. Repeat steps 5 & 6 for this one as well

9. Minimize but DON'T CLOSE everything; Now go to your Desktop

10. Right-click on anywhere on your desktop and select: Create Document > Empty File and name it something you will remember, like KEYFILE.

11. Open the KEYFILE


12. Back on the webpage click the highlighted portion of: 

*This repository is signed with  1024R/2F021AC1*

13. On this new webpage click on the higlighted portion of: 1024R/2F021AC1

Now you see a whole bunch of "Hieroglyphics"

14. Copy everything that is NOT at the top of the page, bold, and oversized. In other words, copy **ONLY** this:

[B]-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXgCHAEEALIft85AjPrpngbLA+zRPiMBT/gEO2Dr/wkABeRcx/AQLVEAE4te7VMVAlJ0
nUVHNuL9955evX+0vuL4iqeUUBh7Ufan3BRPv0ryzLtDAZYfxb4F0Jya/XoMgYA6mxNFshvt
gg9EDrvNVEqIhfI0BeBBqy45k/NKa31Qnu8C0OU1ABEBAAG0FUxhdW5jaHBhZCBQUEEgZm9y
IEtvd4i2BBMBAgAgBQJJeAIcAhsDBgsJCAcDAgQVAggDBBYCAwECHgECF4AACgkQDklNuy8C
GsEAWQP/QTthVWFM+7AhMY7r8mkMEXmbnRR97boIL8glQX5QKzKHpcCvd6kOqVcYsBz6eAMr
yBjRosVw4f01q9pvqvoAqX3UVgCBaaNG+N0uK5JmKAK+4c6fWGrm1ODZitvKdN60AnkazDaU
excHeV6AtNQrUMpQeHpYcAnnWHjMV4Ybolc=
=bmqW
-----END PGP PUBLIC KEY BLOCK-----[/B]


15. Paste this into your KEYFILE on the desktop. Save & Close. You can also close that weird looking webpage as well.

16. Back in Software Sources, select the Authentication tab

17. Select Import Key File

18. Now browse the KEYFILE you made on the desktop and select OK.

There should now be a third Item there stating something like "Launchpad PPA for Kow"

19. Click Close, and when a new box pops up, click Reload and wait for Ubuntu to do its thing and it will close automatically.

20. Now go back to Add/Remove Applications and try re-adding VLC. You can now delete the KEYFILE as well.

You should now have a "pre-release" version of VLC 1.0.0

Test it out with an AVI file or DVD. Also you can select Help and About and it should say something like:  1.0.0-pre1 Goldeneye

I noticed the video's in Fullscreen mode tend to "chop" when I move my mouse while its playing the movie. But its a Alpha/Beta version of VLC and are still working the bugs. But I can happily live with it because that lousy Separated screen is gone!!

this worked great, thanks!  is there any need to remove the software sources added?

---

### Post by The Pinny Parlour on 2009-05-01
The pause and skipping in vlc and totem happens to me as well on a clean, fresh install on a desktop.  Is giving me the chits I tell you.  Downgrade will happen this weekend because this issue is unacceptable.

---

### Post by rfurman24 on 2009-05-02
This works great. Thanks.

---

### Post by Nat90 on 2009-05-02
VLC stopped working; when I open the files, the program opens, but it doesn't play anything,

any clues?

---

### Post by thane1 on 2009-06-02
Super  --- Thanks!  I've been trying to get the public key problem for the repo sorted to no avail.  So it was great to find an easy tutorial on getting this repo working.  My VLC 1.0.0 works far better than the 0.9.9a did - no more split screen and disappearing video.  Thanks again.

---

### Post by motang on 2009-06-04
Thanks, updating VLC via PPA fixed the annoying problem.

---

### Post by bobsmith2 on 2009-06-16
> **Nat90 said:**
> VLC stopped working; when I open the files, the program opens, but it doesn't play anything,

any clues?

I have the same issue. Did you ever figure it out? 

To recap, I installed the latest version (1.0.0~RC3), and that did fix the two-window problem, but it left me with two problems:

1) As you said, the program opens and it doesn't play anything at all - it either just sits there, or it crashes.
2) The interface is very ugly and primitive looking - like something from the early 90s. It looks like an old DOS window or something.

So I blew away the repository, uninstalled 1.0.0, and then reinstalled 0.9.9a. I still have two windows, and it still looks like crap, but at least it plays videos.

---

### Post by tanha on 2009-06-27
When subscribing to [https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa) , does it get updates of any kind, for example security or bugs?

---

### Post by Damon68 on 2009-06-27
Thank you Greg Xix,

Worked like a charm :)

Damon

---

### Post by cotcot on 2009-07-30
Thanks. The bug is indeed solved in 1.0.1

---

### Post by Elep.Repu on 2009-08-06
> **Greg Xix said:**
> 
[https://launchpad.net/~kow/+archive/ppa]("https://launchpad.net/%7Ekow/+archive/ppa")




Thanks for the link, very much.

---

### Post by joshzam on 2009-08-26
I wasn't able to import the key file by creating the text file and importing from Software Sources. It just wouldn't recognize the file as a valid key. But this did work for me:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys 2F021AC1
gpg --armor --export 2F021AC1 | sudo apt-key add -
```

---

