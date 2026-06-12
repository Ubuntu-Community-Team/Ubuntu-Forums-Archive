---
title: "Now on Feisty, still no sound"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by Rhapsody on 2007-04-25
For a while now, I've been using an ASRock K8NF6G-VSTA with what the motherboard refers to as a 'Realtek ALC861VD/ALC883' (which seem to be two separate pieces of hardware) on Edgy Eft. This didn't work very well, as Edgy Eft failed to detect it. I was told Feisty Fawn worked well on this motherboard, so I tried it.

Now I'm on it, and it seems to know the hardware, since KMix and alsamixer now work properly. Problem is, still no sound. Seriously, I start Amarok, play a file, turn my speakers right up to the maximum, and get absolutely nothing.

One thing I can think of is that I'm not very familiar with this motherboard. Since I've never gotten sound out of it, I can't be certain that I've set everything up correctly. The system actually comes with **eight** sockets that my speakers will go in to. The two 'Mic' sockets can be eliminated quickly, as can 'Line In'. The headphone socket is likely not what I want (since they're for headphones, and I'm using stereo speakers). This leaves 'Front', 'Centre', 'Side', and 'Rear'. I'm guessing 'Front' is the correct one, and alsamixer indicates that it's turned up to 81, which is good.

So now I'm stumped. It's impossible for me to even tell that both the sound hardware and speakers even ***work***, since I've have never, in three whole months, ever gotten any version of Kubuntu to give me any sound whatsoever. I doubt they are broken though, so I'm giving this one more go.

---

### Post by Rhapsody on 2007-04-26
While some of you may have thought this problem would fix itself, hence there being no need for you to even acknowledge the existence of this topic, it has not and I'm still getting no sound. In fact, adding up the time since the sound broke on my old PC right up to now (a continuous timeline of no sound from any PC) it has now been **five whole months** since I first had this problem. Yes, this problem has now spanned **TWO YEARS**.

---

### Post by nicky.7 on 2007-04-26
I have the same problem... ([http://ubuntuforums.org/showthread.php?p=2538770](http://ubuntuforums.org/showthread.php?p=2538770)) 
No solution at all?
Have you tried to fill a bug? We can try... Have you tried some other distros with the same card (in order to know if it is a kernel problem or not..)
Thanks.. Nicola

---

### Post by Beliar on 2007-04-26
Hi, I also had a lot of problems with my sound on Linux since years. But I solved the issue for me kind of, there are tutorials on the net. Though thats not a "fix" that would help everyone, just a local workaround.

You have a sound card/code from Realtek, those in different variants are very common and based on the Intel HD Audio design. I have also a similar one in my Asus Notebook.

The Problem is, that the snd-hda-intel driver is activated and everything, but it seems to use the wrong model. since there are different models implementing that Intel HD Audio spec. For instance, I had sound with my Notebook speakers, but not with the headphone.

You can change the model used by the driver with and option and I would also recomend another option that solves a problem with noisy sound.
The Problem is, I dont know what exact model you need. So we can try it out if you have the patience, or google knows the answer.

It would help if you could tell me what jacks you have. E.g, I have 1 Line-In, 1 Microphone jack and an SPDIF combo jack for outgoing sound. Its an spdif it glows red (in windows, in linux you have to activate that optical output).

you can change it like this:
Open the command line
cd /etc/modprobe.d/
sudo nano alsa-base

and at the end you make a new entry and write:
options snd-hda-intel model=z71v position_fix=1

Attention, thats what _my_ line looks like. You can try it, I dont think it would brake anything, but if it doesnt work, no panic, there are plenty of models ;)

The change will work when the sound system is restarted, you can do that by typing that into the command line:
sudo /etc/init.d/alsa-utils restart

After that, your sound might be muted, so try to put every slider up and unmute them. 

On my notebook, its kinda strange, after doing that, I have a slider for PCM and a slider for the Headphones. PCM regulating the "total" sound and the only one needed with speakers, but with headphones, its like regulating between zero and the PCM value. So I have to put up both to make it louder, but thats not so terrible...

Here a list of models, you can find them in /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
(At the snd-hda-intel section)

3stack        3-jack in back and a headphone out
          3stack-digout 3-jack in back, a HP out and a SPDIF out
          5stack        5-jack in back, 2-jack in front
          5stack-digout 5-jack in back, 2-jack in front, a SPDIF out
          6stack        6-jack in back, 2-jack in front
          6stack-digout 6-jack with a SPDIF out
          w810          3-jack
          z71v          3-jack (HP shared SPDIF)
          asus          3-jack (ASUS Mobo)
          asus-w1v      ASUS W1V
          asus-dig      ASUS with SPDIF out
          asus-dig2     ASUS with SPDIF out (using GPIO2)
          uniwill       3-jack
          F1734         2-jack
          lg            LG laptop (m1 express dual)
          lg-lw         LG LW20/LW25 laptop
          tcl           TCL S700
          clevo         Clevo laptops (m520G, m665n)
          test          for testing/debugging purpose, almost all controls can be
                        adjusted.  Appearing only when compiled with
                        $CONFIG_SND_DEBUG=y
          auto          auto-config reading BIOS (default)

By the way, thats not an Ubuntu flaw. I had this issue with gentoo too, the driver option auto just does not pick the correct model.

Hope I could help you,
greets, 
Beliar

---

### Post by Beliar on 2007-04-26
Looks like there is also a wiki page about that:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

They actually say the same as me. But there are some more descriptions to models I dont know.

---

### Post by bigdidz on 2007-04-26
I had the same problem and just did what they say there [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

For me it was the `alsamixer` that was mute.

---

### Post by Rhapsody on 2007-04-26
Beliar: Looks like there are a fair few combinations to try there. It certainly looks like I've got the '6stack' setup though (6 jacks at the back, 2 at the front). No luck with my current attempts though.

I also have to think that if there's any good argument against 'Linux desktop readiness', this may be it. You can argue about different interfaces and ways of thinking all you like, I'm more determined than average and I'm on the verge of giving up on this one. It's not like this is an esoteric bit of hardware either, this is a common type of motherboard!

---

### Post by Beliar on 2007-04-26
yeah I know :/  It drove me crazy too. I'm listening to music _all_ the time with headphones. Headphones not working is quite a killer and drove me into booting windows more often.

But thats a "bug" in the alsa driver or by the hardware manufacturer (firmware/bios issue? i have no clue). I had a look at the ALSA dev site, but it was quite confusing, I guess I'll have to bite into the sour apple and get registered and try to file a bug report.

You have also to be sure, that the sound is not muted! Thats the default after restarting ALSA AFAIK.
Maybe you want to try the z71v model. I have that, though I have a notebook. But I saw quite a lot people having different hw than me using that. 
Or you might try the asus ones (which wouldnt work with my asus notebook).

Goodl luck. And dont give up on Ubuntu too fast ;) Its getting better and better and it has quite some handy features. And you surely want to be fit for an alternative, when vista is the only option left. I would want to use vista gah x|

---

### Post by Rhapsody on 2007-04-26
I've checked KMix and alsamixer, and found that they're both not muted. Everything gives the indication that it's set-up right and working properly, but I still get no sound. It's especially frustrating as there's no indication of a problem, hence nothing to fix.

Also, I don't really plan to give up on Ubuntu entirely, but it seems my choices now are limited. What the hell am I supposed to do? Wait for Gutsy Gibbon and hope that fixes it? By that point, I'll have been without sound for **NEARLY A YEAR**. Say what you like about Windows, I'd have sound if I were still using Windows XP right now. I may have had to hunt down and install drivers, but that'd be child's play next to what I'm trying to do here.

---

### Post by steven8 on 2007-04-27
You have tried both front and back jacks?  My mobo said that if I connect the front jacks, it would disable the rear.  so I left them disconnected.

If you have an open pci slot, get a cheap soundblaster.

Oh yes.  Is the sound enabled in the bios?

---

### Post by deadgobby on 2007-04-27
[http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

---

### Post by Rhapsody on 2007-04-28
> **steven8 said:**
> You have tried both front and back jacks?  My mobo said that if I connect the front jacks, it would disable the rear.  so I left them disconnected.

No, but it would seem there's little problem in the rear jacks being disabled as I only have two speakers (both connected to the front jacks).

> **steven8 said:**
> If you have an open pci slot, get a cheap soundblaster.

I've been resisting that for a while, and I don't intend to finally go down that route now that Ubuntu actually supports this stuff. I'm not going to stop banging my head against this wall.

> **steven8 said:**
> Oh yes.  Is the sound enabled in the bios?

You know, I haven't checked. This is an ex-rental PC, so I assumed it would be enabled already. I'll check on my next reboot.

---

### Post by steven8 on 2007-04-28
> No, but it would seem there's little problem in the rear jacks being disabled as I only have two speakers (both connected to the front jacks).

Then it's possible the person who set up the motherboard may have not connect the front jacks.  Odds are they did, but you never know.

> You know, I haven't checked. This is an ex-rental PC, so I assumed it would be enabled already. I'll check on my next reboot.

It's always worth a look.  If they ever had a soundcard in there, they'd have to disable onboard sound to use it.

---

### Post by Rhapsody on 2007-05-01
I've now checked the on-board audio in the BIOS. It was set to 'Auto', so I decided to be certain and set it to 'Enabled'. No effect. The steps detailing how to make ALSA work again after a Feisty upgrade also haven't gotten my any progress.

No idea where to go from here.

---

### Post by josephus on 2007-05-01
which version of alsa are you trying.  it never hurts to compile the latest version of alsa from source (they are up to 1.0.14rc3, and feisty is 1.0.13).

---

### Post by josephus on 2007-05-01
rhapsody: this guy has the same motherboard as you and got his sound working by using 1.0.14rc3 and

options snd-hda-intel model=3stack

[http://ubuntuforums.org/showthread.php?p=2467125](http://ubuntuforums.org/showthread.php?p=2467125)

---

### Post by steven8 on 2007-05-01
> **josephus said:**
> rhapsody: this guy has the same motherboard as you and got his sound working by using 1.0.14rc3 and

options snd-hda-intel model=3stack

[http://ubuntuforums.org/showthread.php?p=2467125](http://ubuntuforums.org/showthread.php?p=2467125)

Ooh.  Did that work for you, Rhapsody?

---

### Post by VuDu on 2007-05-02
I have an ASUS A6Vc and I have to add that line to modprob.d/alsa-base each time I make a fresh install of Ubuntu.
Shouldn't a bug be filled to fix that? I guess it's supposed to detect the right model by itself, no?

---

### Post by Eddie Wilson on 2007-05-02
The last version of Ubuntu I had that had no sound problems was Dapper. But that may not be Ubuntu,s fault. I have received no help from my post at all on my problem. Can't get anyone to answer.
eddie

---

### Post by treaz on 2007-05-11
> **josephus said:**
> rhapsody: this guy has the same motherboard as you and got his sound working by using 1.0.14rc3 and

options snd-hda-intel model=3stack

[http://ubuntuforums.org/showthread.php?p=2467125](http://ubuntuforums.org/showthread.php?p=2467125)
This has worked perfectly for me and the only thing I had to do was to modify alsa-base, I didn't upgrade to 1.0.14.

---

