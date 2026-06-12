---
title: "Firefox hangs with javascripts and flash"
date: 2010-03-14
forum: Multimedia Software
---

### Post by jakslev on 2010-03-14
I use Ubuntu 9.10 64 bit, completely updated. 
My browser is Firefox 3.5.8

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.8) Gecko/20100214 Ubuntu/9.10 (karmic) Firefox/3.5.8 GTB7.0

I am unable to open pop-up windows linked with java. Also the flv videos on Youtube are often un-responsive or requires several clicks to play. 

I have a suspicion this is related to Google Toolbar or maybe Chrome Extreme Firefox skin?  

Note: I have reinstalled Ubuntu several times and tried both 32-bit and 64-bit, as well as the new 10.04, beta2. 

Anyone else with problems like this?

---

### Post by Bob63 on 2010-04-14
> **jakslev said:**
> I use Ubuntu 9.10 64 bit, completely updated. 
My browser is Firefox 3.5.8

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.8) Gecko/20100214 Ubuntu/9.10 (karmic) Firefox/3.5.8 GTB7.0

I am unable to open pop-up windows linked with java. Also the flv videos on Youtube are often un-responsive or requires several clicks to play. 

I have a suspicion this is related to Google Toolbar.  

Anyone else with problems like this?

I am using LinuxMint 8 Helena Main, which is based on Ubuntu 9.10. x86 (32-bit distro).

There seems to be an on-going problem that is affecting the Flash video playback in FF. This is occurring in at least one other distro that I am aware of, so it is not an Ubuntu-specific issue. The Flash problem ***seems*** to be caused by PulseAudio.

I do not have the Google toolbar installed and I also experience the same problem with Flash.

My system is currently up-to-date, my FF version is 3.5.9 and my FF Java plug-in is v1.6.0_15. and I have no problems with Java/Javascript.

---

### Post by khawari on 2010-04-14
> **Bob63 said:**
> I am using LinuxMint 8 Helena Main, which is based on Ubuntu 9.10. x86 (32-bit distro).

There seems to be an on-going problem that is affecting the Flash video playback in FF. This is occurring in at least one other distro that I am aware of, so it is not an Ubuntu-specific issue. The Flash problem ***seems*** to be caused by PulseAudio.

I do not have the Google toolbar installed and I also experience the same problem with Flash.

My system is currently up-to-date, my FF version is 3.5.9 and my FF Java plug-in is v1.6.0_15. and I have no problems with Java/Javascript.

I had the same problem, it hanged out i had to restart firefox! 
My friend fixed it for me, don't know what he did, he works in tauros media, you can contact him and ask the issue that he helped me (khawari) and he'll understand:P

Cheers!:)
 [FONT=&quot][http://www.taurosmedia.com]("http://www.taurosmedia.com/")[/FONT]

---

### Post by Bob63 on 2010-04-14
> **khawari said:**
> I had the same problem, it hanged out i had to restart firefox! 
My friend fixed it for me, don't know what he did, he works in tauros media, you can contact him and ask the issue that he helped me (khawari) and he'll understand:P

Cheers!:)
 [FONT=&quot][http://www.taurosmedia.com]("http://www.taurosmedia.com/")[/FONT]

Thanks for the offer. I checked out the tauros site and noticed it is written in Dutch. Does your friend understand English, because I only read/write English? What is his name so that I can address him?

---

### Post by jakslev on 2010-04-15
> **khawari said:**
> I had the same problem, it hanged out i had to restart firefox! 
My friend fixed it for me, don't know what he did, he works in tauros media, you can contact him and ask the issue that he helped me (khawari) and he'll understand:P

Cheers!:)
 [FONT=&quot][http://www.taurosmedia.com]("http://www.taurosmedia.com/")[/FONT]

Yes - please, if you have a solution please post it here. I am starting to think it might be related to the ATI graphics card on my notebook as it doesn't happen on any of my nvidia machines.

---

### Post by Bob63 on 2010-04-15
> **jakslev said:**
> Yes - please, if you have a solution please post it here. I am starting to think it might be related to the ATI graphics card on my notebook as it doesn't happen on any of my nvidia machines.

jakslev,

I am running a relatively new nVidia card [9500GT] with the most current driver which has lots of memory - 1GB - and I have this problem. The logs on my machine seem to indicate that it is a PulseAudio problem. I have many lines in my messages log like this:

```
bob63-desktop pulseaudio[2525]: ratelimit.c: 852 events suppressed
```Also, during the slowdown my cpu usage in the system monitor jumps from approximately 25% to 90% or more, and the "guilty" thread is pulseaudio.

There are many threads on similar topics here and in the LinuxMint forums that all seem to be related, but I have not seen a fix or workaround yet.

---

### Post by jakslev on 2010-04-16
I see. The strange thing is that this also happens if/when I try to open images that are "activated" by javascript. For instance if I click on a picture here: [http://www.beretta.com/Long-guns/Field-guns/Over-and-Unders/SV10-Perennia-III-Optima-Bore-HP/index.aspx?m=82&f=2&idv=1&id=2](http://www.beretta.com/Long-guns/Field-guns/Over-and-Unders/SV10-Perennia-III-Optima-Bore-HP/index.aspx?m=82&f=2&idv=1&id=2). 

I would find it strange if pulseaudio should play a role in this, but I will have a look at LinuxMint all the same. 

Thanks,

jakslev

---

### Post by Bob63 on 2010-04-16
> **jakslev said:**
> I see. The strange thing is that this also happens if/when I try to open images that are "activated" by javascript. For instance if I click on a picture here: [http://www.beretta.com/Long-guns/Field-guns/Over-and-Unders/SV10-Perennia-III-Optima-Bore-HP/index.aspx?m=82&f=2&idv=1&id=2](http://www.beretta.com/Long-guns/Field-guns/Over-and-Unders/SV10-Perennia-III-Optima-Bore-HP/index.aspx?m=82&f=2&idv=1&id=2). 

I would find it strange if pulseaudio should play a role in this, but I will have a look at LinuxMint all the same. 

Thanks,

jakslev

jakslav,

Concerning your java/javascript issue: are the site(s) you visit permitted to open pop-ups by Firefox? Edit>Preferences, Content tab, java and javascript options checked? Do you have any script-blocking add-ons (such as NoScript), or AdBlock installed? NoScript blocked some scripts in the link you provided.

I have noticed with both of these add-ons that they can be very aggressive when blocking content in web pages. I occasionally have to manually refresh a page when I tell NoScript to allow a webpage to execute a script, or even close a tab then re-click on a link so that the page will display content correctly. On a few pages I have visited, even after I have told NoScript to allow everything on a page in an effort to get content to display correctly, I have found out that Adblock is what finally had the content blocked. Only by disabling AdBlock on the page did the content displayed.

As for the flash content issue, take a look at:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Yesterday I followed the procedures in the first post of this thread, which updated the alsa drivers and some odds and ends. I have (so far) been watching flash content without the skips and lock-ups which have been plaguing my system. If the problem resurfaces I will post here.

---

