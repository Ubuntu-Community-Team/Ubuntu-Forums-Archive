---
title: "I find why sound recorder and skype don't work?"
date: 2009-10-09
forum: Multimedia Software
---

### Post by ivra on 2009-10-09
Hi,

I used Ubuntu since 5.04 and last was 8.04. I have problem to use my microphon on my laptop. I have HDA-Intel-HD ATI SB (ALC833). I read alot of tutorials in this forum, how to ...with pulseaudio, with esound and I can't record sound or use microphon to speak on Skype. So when I want to record something I used one live CD "dyne:bolic" GNU/Linux based on Debian. And It was perfect. I don't use Skype on it.

So I take a decision to install Debian Lenny 5.0.3 and to check on it. I use usb wifi D-link G122 C1 which is plug and play on Ubuntu and it's perfect. 

I was very happy when use sound record and my voice was recorded. And decided to put my wifi usb and to check the Skype. .... Nothig happend Lenny do not recognaize my Wifi. So put back my internet cable in the laptop and find on Debian wiki (very good wiki) that you must install ralink from non free. "Ok" - I say - "It's not like Ubuntu. It's not auto." So read the instruction and after 1 minute my usb Wifi was up.

I check sound recorder incidentally - Not working any more. No voice - nada, zero.

And for the first time I realize and see it ( I am not a programmer or geek) that beatween rt73usb driver and my microphon and sound recorder that there are connect.

I remove the driver ( I can't use the wifi) restart the OS and every thing work perfect again. Install Skype ( I must install from repo Gdebi as well) and skype work perfect for me for the first time.

So I have working laptop with no wifi. So my laptop lose mobility. 

Does somebody try it and have experiance with that and How can be resolved this. 

Thanks

P.S. My English is ot native. Exuse me.

---

### Post by RichardLinx on 2009-10-10
Did you completely remove pulse audio when you installed esound? If you did there's a chance that you had conflicting packages (though unlikely, I guess it's worth mentioning). After you remove pulse audio and install esound you should run:
```
apt-get autoclean
```
```
apt-get autoremove
```
If that wasn't the issue at all you *might* have some luck by playing around in the bluetooth settings. (Though I doubt it because there isn't too much there)

Also, you mentioned that the last version of Ubuntu you used was 8.04... From experience I can say that sound never seems to work right in 8.04.x You'll probably have more luck with 9.04.

As for Debian - you'll probably have more luck over at the official Debian forums.

---

### Post by ivra on 2009-10-10
hi RichardLinx,

Yes I try this. Nothing happened. I have a lot of trouble with pulseaudio. I try 9.04 as well, but I read that in latest version of Ubuntu there are a lot of dependence with pulseaudio and in 9.10 are more. 

So for me work perfect when remove rt73usb driver with pulseaudio or esound. When rt73usb driver is on gnome sound record freeze and Skype too. 

In Ubuntu rt73usb is by default, so I never think that maybe the problem is it. 

Thanks for replay

---

### Post by ivra on 2009-10-11
So If Somebody can help me,
to resolve this or try to do it?

Sincerely,

ivra

---

### Post by ivra on 2009-10-13
Hi,

I install Ubuntu 9.04. After remove module from kernel rt73usb and rt2x00usb everything work fine. My internal mic was found and I am capable to record sound and use skype. 

Before remove the PulseAudio Volume control freeze. After that -> ok.

So I found one internal wifi for my laptop and I think that should use other driver rt, so when I received I will try.

I need to record sound and use Skype only for my work at home. So I will try to make a script ( first learn how) when i use skype automatic to remove the modules for the session.

Have a nice day.

---

### Post by ivra on 2009-10-20
Hi, 

My experianse until now. So I used to put rt73usb and the dependence rt2x00usb and etc. to the blacklist of kernel modules. So everything work fine until one day (yestarday) when everything broke again. And I can't use my mic anymore. I try to remove pulseaudio and install esound (I found tutorials in this forum) and after the restart everything is ok again (I miss the gnome pulseaudio stuff).

After cuple of hours everythign broke again. No more mic no more record sound. 

I install 2-4 programs but I don't expect this, so I don't know witch program made the broke ( I hope you understand my lang).

I am on the Blue Desk again I do not have clue anymore.

P.S.

I use MSI Megabook S420

---

### Post by ivra on 2011-05-14
Hi,

Now I use 10.04 - Lucid. I found that if I put in alsa-base.conf the line: options snd-hda-intel position_fix=1 my internal mic start to work.

I hope this fix my problems and to continue to work without bugs.

---

