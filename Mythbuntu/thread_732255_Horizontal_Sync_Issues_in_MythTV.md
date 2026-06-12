---
title: "Horizontal Sync Issues in MythTV"
date: 2008-03-22
forum: Mythbuntu
---

### Post by trirnoth on 2008-03-22
I'm having issues watching TV through MythTV that I do not have under tvtime.

The best way to describe this is with a picture: [http://users.evenlink.com/ubuntu/screenshot.png](http://users.evenlink.com/ubuntu/screenshot.png).
Basically getting green colors with multiple images/ horizontal sync issues.

When changing channels, it looks fine for a second. 
When recording, the thumbnail showing in recordings looks great.

Ubuntu 7.10 Gutsy Gibbon 2.6.22-14-generic with an ATI TV Wonder Pro.
Native resolution is 1920 x 1200.

I played around with adding modlines in my xorg.conf (shown below) per [http://www.mythtv.org/docs/mythtv-HOWTO-22.html](http://www.mythtv.org/docs/mythtv-HOWTO-22.html).
I tried the aspect ratio fix listed at [http://www.mythtv.org/wiki/index.php/Aspect_ratio](http://www.mythtv.org/wiki/index.php/Aspect_ratio)
Also with Aspect Ratios in MythTV/ Settings/ Apperance but I always end up with the same results.

I found the page located at [http://www.mythtv.org/wiki/index.php/ATI_TV-Wonder](http://www.mythtv.org/wiki/index.php/ATI_TV-Wonder) regarding color issues but (could be wrong) do not feel like this is the problem - at least with the hsync.

The rest of this is output that I'm hoping is relevant:

# cat /etc/modprobe.d/bttv
options bttv card=37 tuner=2

# lspci
00:0e.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0e.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

# grep modeline /etc/X11/xorg.conf
        modeline        "1920x1200" 154.0 1920 2056 2256 2592 1200 1203 1209 1245 -hsync +vsync interlace
        modeline        "768x576"   35.00  768 800 872 976  576 579 583 599 -hsync +vsync
        modeline        "800x600"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
        modeline        "640x480"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync

# dmesg
[   23.308000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 21
[   23.308000] bttv0: Bt878 (rev 17) at 0000:00:0e.0, irq: 21, latency: 64, mmio: 0xefe00000
[   23.308000] bttv0: using: Prolink PixelView PlayTV pro [card=37,insmod option]
[   23.308000] bttv0: gpio: en=00000000, out=00000000 in=00ffc0ff [init]
[   23.312000] bttv0: using tuner=2
[   23.312000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   23.312000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   23.316000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   23.780000] lirc_dev: IR Remote Control driver registered, at major 61 
[   23.808000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   23.808000] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   23.808000] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   23.808000] tuner 0-0063: chip found @ 0xc6 (bt878 #0 [sw])
[   23.816000] ovcamchip: v2.27 for Linux 2.6 : OV camera chip I2C driver
[   23.828000] usbcore: registered new interface driver xpad
[   23.864000] bttv0: registered device video0
[   23.864000] bttv0: registered device vbi0

Thanks if you made it this far.

Regards,
t

---

### Post by laga on 2008-03-22
Can you play other video files with MythTV? I'm wondering if this is a recording problem or a playback problem.

---

### Post by trirnoth on 2008-03-23
Thanks for the response laga.

I had honestly not even thought to install MythVideo to test so excellent question.

Hard to tell in the screenshot I provided but there is a line that goes from top-left to bottom-right.

Just installed and Yes I can play other videos. However, while the picture is much better than TV, that line is there and it appears that each triangle has a different timing.

I guess this takes me in a different direction of things to look for - just what I do not know.

Thanks again,
t

---

### Post by KillerKiwi on 2008-03-23
I had an issue like this and it was the play back settings

I muddled my way though the new playback screen and changed it to normal and it seems fine now

I was able to confirm it was playback by playing recordings from before the upgrade

---

### Post by trirnoth on 2008-03-23
KillerKiwi: Thanks as well for the reply.

Just to verify:
- This is a clean install, not an upgrade.
- Your statement regarding playback settings, You are speaking of those within the frontend under Utilities Setup / Setup/ Appearance/ Screen Settings and Video Mode Settings?

I did try different settings in both of the above and I'm always left with the same problems/ results.

Anyone out there have a widescreen monitor have these settings they would like to share? Or state that they didn't have to do anything with these so I can discount this as the problem?

Regards,
t

---

### Post by trirnoth on 2008-03-24
The more I poke around and read through forums, the more I believe I am having three separate issues that I initially thought was one.

1. Some update, whether due to Myth or Ubuntu itself is causing the diagonal line.
I just noticed the same problem when viewing video outside of Myth through vlc, totem,mplayer, ... Something that did not occur before.
Possibly a codec addition or update?

2. The way Myth is reading my TV Tuner is causing the horizontal sync issues since this works with tvtime.

3. The green hue when viewing TV. I feel that fixing #2 will either fix this or make it where the mysql change at  [http://www.mythtv.org/wiki/index.php/ATI_TV-Wonder](http://www.mythtv.org/wiki/index.php/ATI_TV-Wonder) will work.

Obviously any ideas are welcome though it may end up that I work on #1 and go back to viewing TV and videos without the Myth Interface.

Regards,
t

---

### Post by Verbatim9 on 2008-03-24
I ran into a similar problem recently...I've been trying to troubleshoot some random crashes of my frontend and something I found suggested that they might be OpenGL related, so I attempted to turn off OpenGL vertical sync...which resulted in strange vibrant colors and bad positioning of the video, quite similar to your screenshot.

So I'd try turning on OpenGL vertical sync in Settings->TV Settings->Playback...here's hoping it works and remains stable for you.

---

### Post by trirnoth on 2008-03-24
Thanks Verbatim9.
I had been reading some forums regarding settings to OpenGL when looking into my sync issues, though would not have found the settings in Myth - so thanks for pointing me there.

I didn't state before, though should have, that I am using an NVidia graphics card. Not sure if I read everything about this issue, but those that stated this fix were for ATI.

This ended up changing TV from green to a purple hue with the same skipping.
The diagonal line was still there for TV as well as video.

Again. Thanks for the thought. Tonight I'll have some more time to work on this so hopefully I'll be able to update this thread with something positive.

Regards,
t

---

### Post by Verbatim9 on 2008-03-24
Well, I've got an update on the status of my system...in "playback profiles" (that's page 3 of Settings->TV Settings->Playback), I switched to the "slim" preset, and everything is working just the same as it did under MythTV .20, playback works fine again.  After making the change I had to re-boot my system, for some reason playing around with those settings had confused the heck out of MythFrontend (everything was playing green all the time after playing with those settings, even when I put them back to how they had started out), but switching to "slim" and then rebooting my computer has got things working smoothly again.

I've got an old issue back (which I had in .20) that some TV stations' programs loose synching between the video and audio (FOX in particular), but there are no more crashes. Pausing and starting the program again gets the synch back, and it doesn't happen so often that it's unberable...but I've found some more settings to tweak, so I'm hopeful it will end up working better than it did in .20 before I'm done playing around with things.

There is actually quite a bit of tweaking that can be done on page three of the playback settings, but most of the settings are a bit hidden away...if you select the "edit" button next to one of the video resolutions in the list, you can change the setting for how video in that group gets played back, the video renderer, the type of de-interlacing, how many CPUs to use for decoding video...a lot of different things that could impact how much CPU power is needed to watch a show, how smooth playback is, and (apparently) how stable MythTV is.

There are a lot more settings in there than I remember seeing in MythTV .20, though some of them are familiar settings that I'd been trying to find but couldn't.

---

### Post by trirnoth on 2008-03-24
Verbatim9 : Wow. Awesome. Thanks!
Setting this to slim and I have a normal picture. I can go up to CPU--, after that I'm back to picture sync and color issues.

This solved numbers 2 (hsync) and 3 (color) on my list!

I'll admit some surprise that this worked. I understand that I don't have the latest/greatest processor available - but it is an AMD Dual Core 2.2 (4200+) and 3 GB RAM.

 I still have the diagonal line but again I do not believe this is a Myth issue.
This opened up a new problem now with sound syncing (about a second off) but I feel I am close.
At the very least I get to work on a new issue which is a nice change.

I'll try more settings under Playback and read the forums regarding sound, but again this is a great feeling being this close.

I can't say it enough but Thanks again,
t

---

