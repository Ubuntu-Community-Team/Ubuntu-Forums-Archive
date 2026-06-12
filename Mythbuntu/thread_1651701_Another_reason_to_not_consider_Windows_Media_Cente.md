---
title: "Another reason to not consider Windows Media Center"
date: 2010-12-23
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2010-12-23
So I [built an HTPC]("http://ubuntuforums.org/showthread.php?t=1587584") and worked my way up to ubuntu 10.10 with mythtv 0.24.

I'm and all [OTA and having problems with the Hauppauge HVR-2250]("http://ubuntuforums.org/showthread.php?t=1645476") reception.

So I snag a Windows 7 64bit Home Premium and a spare hard disk.  I'm curious and think it might help with the reception problem because Hauppauge supports Windows.

When setting up audio, I discover that nvidia drivers only support stereo though the HDMI cable to the television, no 5.1.  What [EVGA says in their web page]("http://www.evga.com/articles/00514/"), "DVI-I and HDMI 1.3a - Dual-link DVI support and HDMI output enables sending both high-definition video and audio signals to an HDTV via single cable."

5.1 works fine with mythtv .23 & .24 on ubuntu 10.10 with the nvidia proprietary drivers.

EVGA tech support is not helping much, probably because it's nvidia that left out 5.1 capability on the 260.99 drivers.

If that's not enough, the reception problems are worse on the Windows 7 Media Center.

---

### Post by keepitsimpleengr on 2010-12-24
> EVGA tech support is not helping much, probably because it's nvidia that left out 5.1 capability on the 260.99 drivers.

Follow-up from EVGA technical support in a phone call:

Paraphrase "The reason nvidia cannot send 5.1 through the HDMI to the television in Windows is because the way Microsoft handles digital audio makes it impossible."

They say it will work if the HDMI goes to the receiver instead of the television.

Mythtv, the Blu-ray player, the HD-DVD player, several DVD players, the Sony PSP3, the satellite dish all do not have this problem, all without fuss send 5.1 to the television, which then sends it to the receiver via optical cable.

It seems unlikely to me that it could send 5.1 to a receiver but not a television. :-({|=

---

### Post by LowSky on 2010-12-24
Sorry but how is a TV going to play 5.1? I don't know of one TV that has 5.1 speakers. You will need an audio receiver, 5 speakers (center, left, right, and two rear) and a subwoofer to get 5.1 sound.

Most newer TV sets have a virtual mode for fake 5.1, but Stereo is the best any TV can really do.

Microsoft's "limitation" is there because the TV cannot actually handle real 5.1 sound.

---

### Post by keepitsimpleengr on 2010-12-25
> **LowSky said:**
> Sorry but how is a TV going to play 5.1? I don't know of one TV that has 5.1 speakers. You will need an audio receiver, 5 speakers (center, left, right, and two rear) and a subwoofer to get 5.1 sound.

Most newer TV sets have a virtual mode for fake 5.1, but Stereo is the best any TV can really do.

Microsoft's "limitation" is there because the TV cannot actually handle real 5.1 sound.

The setup is:

Source&#8943;[HDMI]&#8943;>Television&#8943;[Optical Cable]&#8943;>Receiver

Sources are:

The _Bluray player_ connects via HDMI to the television and I get 5.1

The _HD-DVD player_ connects via HDMI and I get 5.1

The _DVD player_ connects via HDMI and I get 5.1

The _satellite dish_ connects via HDMI and I get 5.1

The _Sony PS3_ connects via HDMI and I get 5.1

The _HTPC with GT240 running Linux_ connects via HDMI and I get 5.1

When using the televisions _built in receiver_, it outputs 5.1 when the OTA transmission provides it.

The _HTPC with GT240 running Windows 7 64 Home Premium_ connects via HDMI and I can only get stereo.

---

### Post by keepitsimpleengr on 2010-12-25
Then latest message from EVGA says the HTPC with GT240 running Windows 7 64 Home Premium connecting via HDMI is not officially supported.

---

### Post by keepitsimpleengr on 2010-12-25
> **keepitsimpleengr said:**
> &#8943;
The _HTPC with GT240 running Linux_ connects via HDMI and I get 5.1
&#8943;
The _HTPC with GT240 running Windows 7 64 Home Premium_ connects via HDMI and I can only get stereo.
&#8943;

:) Linux-x86_64 (Mythtv 0.24-fixes, Ubuntu 10.10) using proprietary nvidia driver version 260.19.06 (nvidia-current)

:icon_frown: Windows 7 using nvidia driver version 260.99, stereo is the only choice offered for the nvidia HD audio setup in the control panel.

---

### Post by LowSky on 2010-12-26
most computers have an optical output for onboard sound, why not try to use that?

---

### Post by keepitsimpleengr on 2010-12-26
> **LowSky said:**
> most computers have an optical output for onboard sound, why not try to use that?

No such "luck".

In any case, I would have to change the input selector on the receiver every time I switched the television to another source than the HTPC, such as it's own receiver or Bluray player, and also no PIP sound likewise.

Fortunately, I'll be using Mythtv :guitar: instead of 
the stunted Windows Media Center on Windows 7 Home "Premium" :-({|= .  

WMC only for testing the HVR-2250.

---

### Post by 4dognight on 2010-12-27
> **keepitsimpleengr said:**
> The setup is:

Source&#8943;[HDMI]&#8943;>Television&#8943;[Optical Cable]&#8943;>Receiver

Sources are:

The _Bluray player_ connects via HDMI to the television and I get 5.1

The _HD-DVD player_ connects via HDMI and I get 5.1

The _DVD player_ connects via HDMI and I get 5.1

The _satellite dish_ connects via HDMI and I get 5.1

The _Sony PS3_ connects via HDMI and I get 5.1

The _HTPC with GT240 running Linux_ connects via HDMI and I get 5.1



I'm curious which TV do you have that has 6 HDMI inputs?

---

### Post by keepitsimpleengr on 2010-12-28
> **4dognight said:**
> I'm curious which TV do you have that has 6 HDMI inputs?

Toshiba 47LX196 pseudo 1080p, it's got two.  Dish, PS3, & DVD players are all history.

HTPC gets one, 2into1 HDMI switch gets the HD-DVD or the Bluray.

---

### Post by uncle hammy on 2010-12-28
> **keepitsimpleengr said:**
> The setup is:

Source&#8943;[HDMI]&#8943;>Television&#8943;[Optical Cable]&#8943;>Receiver

No offense, but that seems completely backwards to me.  I would never even consider not going Source->Receiver->TV.  You're argument that you have to switch the receiver input each time holds no water either, because the way you have it, you have to change the input on the TV each time you switch sources....what's the difference?

Most people would find it desirable to have a different source on the receiver, because any modern receiver allows for different settings for different sources (i.e. crazy high LFE for movies, more balanced sound for music, etc).

Just my 2 cents....worth every penny, I'm sure.

---

### Post by sparkosaurus on 2010-12-28
> **keepitsimpleengr said:**
> The setup is:

Source&#8943;[HDMI]&#8943;>Television&#8943;[Optical Cable]&#8943;>Receiver



I have a similar setup.
Very low cost frontend using:
Free - Old amd 3200+ athlon 64 bit single core pc I had lying around.
$40 - EVGA GT240 graphics card for digital audio over HDMI.
$900.00 - Insignia NS-L46X-10A 46" LCD (THIS STARTED THE WHOLE THING)
$151.00 - panasonic sa-pt480 5.1 surround.

The reasons I like this configuration is that I couldn't spend much on a real receiver for the surround and I like to use the motion smoothing on the tv.  The smoothing adds a second or so lag in the television picture. The tv passes the digital audio straight out the optical jack in theory keeping it in sync with the video (I have not tried it yet as I just purchased the surround yesterday 12/27/10).

My wife can't stand the motion smoothing, so she turns it off all the time.  With this setup I hopefully won't have to worry about manually keeping the audio in sync on the receiver.

---

### Post by keepitsimpleengr on 2010-12-28
> **uncle hammy said:**
>  you have to change the input on the TV each time you switch sources....what's the difference?

The difference is the tuner and the television would both have to be changed, not just the television as is now.

---

### Post by keepitsimpleengr on 2010-12-28
Another update from EVGA:

> Hi Larry, It should work in the following configuration: Video card (HDMI cable) to the receiver, then from the receiver to your TV. However, the only configuration we can guarantee is from the video card to the TV in standard audio (2.0). This can be a driver limitation from NVIDIA's driver, so it might be best to contact NVIDIA. Here is a PDF with the information from NVIDIA regarding known product limitations, how-to's, and more: [http://us.download.nvidia.com/Windows/260.99/260.99_Win7_WinVista_Desktop_Release_Notes.pdf](http://us.download.nvidia.com/Windows/260.99/260.99_Win7_WinVista_Desktop_Release_Notes.pdf). Regards, EVGA Technical Support

Unfortunately, the nvidia PDF download was corrupted and Acrobat reader could not repair it.

Also, the product guide for the EVGA nvidia GT 240 512 GDDR5 where HDMI support is described can no longer be found at EVGA.com.

It's enough to make a person grumpy.

---

### Post by keepitsimpleengr on 2010-12-28
> **keepitsimpleengr said:**
> Also, the product guide for the EVGA nvidia GT 240 512 GDDR5 where HDMI support is described can no longer be found at EVGA.com.

Spoke too soon...

[http://www.evga.com/articles/00514/]("http://www.evga.com/articles/00514/")

---

### Post by uncle hammy on 2010-12-28
> **keepitsimpleengr said:**
> The difference is the tuner and the television would both have to be changed, not just the television as is now.

I am making an assumption here...if your receiver has HDMI in, it has HDMI out and HDMI switching.  So you would not have to switch the TV.  

Everything goes into the receiver -> one line out to HDMI 1 on the TV.  Tv always stays on HDMI 1.

---

### Post by keepitsimpleengr on 2010-12-28
> **uncle hammy said:**
> ...if your receiver has HDMI in, it has HDMI out and HDMI switching...

Alas, no HDMI on receiver.  It's old but the electrons don't seem to mind.

Plus I would need 25' HDMI cables ($13ea) as well as a new receiver ($230).

All this for the privilege of running Windows 7 with Windows Media Center as well as Mythbuntu 10.10/0.24.  Not yet anyway.

I expect nvidia will eventually figure out what needs to be done and actually do something about it. :lolflag:

---

### Post by keepitsimpleengr on 2010-12-28
More stuff from nvidia:

>  4) If there is a device in between your HDTV and your PC such as an **_*audio receiver*_**, HDMI switch or KVM, it may be blocking your HDTVs EDID information from being passed on to your PC and therefore the PC will not be able to synchronize properly.

Emphasis mine.
It's at ["How do I setup my NVIDIA based graphics card to work with my HDTV?"]("http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/popup_adp.php?p_faqid=2593&p_created=1270025972&p_sid=d69NmHik&p_lva=2505&p_li=&p_redirect=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSwxJnBfcHJvZHM9MiZwX2NhdHM9NjEmcF9wdj0xLjImcF9jdj0xLjYxJnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1IRCBhdWRpbyBIRE1J")

---

### Post by tgm4883 on 2010-12-29
> **keepitsimpleengr said:**
> Another update from EVGA:



Unfortunately, the nvidia PDF download was corrupted and Acrobat reader could not repair it.

Also, the product guide for the EVGA nvidia GT 240 512 GDDR5 where HDMI support is described can no longer be found at EVGA.com.

It's enough to make a person grumpy.

I didn't look though it too much, but I was able to open and view that PDF

---

### Post by keepitsimpleengr on 2010-12-29
> **tgm4883 said:**
> I didn't look though it too much, but I was able to open and view that PDF

I could view it in the browser, but it's 50 pages.  When downloaded with Chrome, Firefox and IE8 on Windows XP and ubuntu, xPDF crashed and Acrobat reader 9 and got "…could not repair…".

So then my brain hiccoughed and I printed to PDF from the browser and got a PDF file that Acrobat reader would open&#8943;allowing me to search.

The search had several references to HDMI & HD audio drivers, but nada about 5.1 not being allowed.

---

### Post by keepitsimpleengr on 2010-12-29
It's semi-official.

From EVGA and nvidia forums.

For forum see [http://forums.nvidia.com/index.php?showtopic=188651&st=0&p=1167921&hl=51&fromsearch=1&#entry1167921](http://forums.nvidia.com/index.php?showtopic=188651&st=0&p=1167921&hl=51&fromsearch=1&#entry1167921) and [http://forums.nvidia.com/index.php?showtopic=186862&st=0&gopid=1168205&#entry1168205]("http://forums.nvidia.com/index.php?showtopic=186862&st=0&gopid=1168205&#entry1168205")
 
especially > ManuelG, on 14 December 2010 - 06:20 AM, said:
This unfortunately is by design. Your HDTV has an internal EDID which tells our graphics card what video and audio modes it supports. Currently it is telling our graphics card that it supports stereo only so we are sending stereo. I am trying to get the driver team to allow the user to override the audio settings similar to how you would do it on a consumer elecronic device (ie blu-ray player, Playstation 3,etc.).

EVGA GT 240 will only support stereo when connected per nvidia's instructions.

Harrumph!  [-X

---

### Post by keepitsimpleengr on 2010-12-30
The solution to this problem can be found at:

[http://thegreenbutton.com/forums/p/96917/508997.aspx#508997](http://thegreenbutton.com/forums/p/96917/508997.aspx#508997)

---

