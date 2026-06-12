---
title: "Apparently not an authorized copy of Ubuntu."
date: 2010-01-01
forum: Multimedia Software
---

### Post by Evie~ on 2010-01-01
[I][FONT=Century Gothic][SIZE=1]About 10 minutes ago, I was about to burn 12 mp3's onto a CD via Brasero, and I got this message about it being an unplayable format or something. :-|

So, I check out the Ubuntu Software Centre to see if there's any plugins/codecs I can grab, because even RythmBox and Movie Player won't play them. ](*,)

I can't download ANY application or anything, let alone codecs from the Software Centre. There's just that little loading circle thing next to anything I click on. No download links anywhere. So I click 'Report A Problem' and wait for it to send something. After 15 minutes of nothing happening, I click cancel about 30 times until this little message pops up: "This is not a valid copy of Ubuntu." 

:mad:!

I downloaded this copy of 9.10 off the Ubuntu website and copied it onto a disc, everything's been going fine. What's wrong with it? :confused:[/SIZE][/FONT][/I]

---

### Post by lovinglinux on 2010-01-01
Have you checked the integrity of the Ubuntu downloaded ISO with the hash number before installing?

See these:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
[http://ubuntuforums.org/showthread.php?t=290339](http://ubuntuforums.org/showthread.php?t=290339)

How are you trying to burn those mp3 files? I don't use Brasero, but you should be able to burn them as data, without needing any codec. I don't know if Brasero has an option to burn an audio CD, but in this case then I guess a codec could be needed.

If this is the case, then see the [Comprehensive Multimedia & Video Howto ](http://ubuntuforums.org/showthread.php?t=766683).

About the connection problems, do you have browsing issues too? If yes, then you could disable ipv6. Unfortunately, I don't know how to do that for the entire system, but on Firefox you can do it by accessing **about:config** in the address bar and setting the option **network.dns.disableIPv6** to true. See if it improves browsing speeds.

About the "Report A Problem" you can find alternative methods at [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) 

Anyway, I would check the CD you used to install Ubuntu to see if there is any corruption. If the hash number don't match, then you will need to download it again and burn a new copy

---

### Post by Evie~ on 2010-01-01
Hey, thanks for your help :)

Yeah, everything on the disc is fine, or so it seems. I only have Brasero, and I can't get any other app to burn my music. Everything says that .mp3 files aren't suitable for audio or video. Argh :(

EDIT: Nope, browsing is all fine, I sorted out that problem pretty quick :)

EDIT 2: No worries, burned it onto a disc via Data, not Audio. Hopefully it plays...

---

### Post by sgosnell on 2010-01-01
It will play on some, but not all, players.  Newer devices will play .mp3 files fine, but older ones require .cda, which is the audio CD standard.

---

### Post by MooPi on 2010-01-01
Your in need of mp3 codecs correct? Open a terminal and copy this command.

```
sudo apt-get install lame mpg123
```

This should allow you to play and record music to mp3.

---

