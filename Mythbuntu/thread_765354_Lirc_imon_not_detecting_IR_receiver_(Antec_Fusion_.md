---
title: "Lirc_imon not detecting IR receiver (Antec Fusion V2 - with knob)"
date: 2008-04-24
forum: Mythbuntu
---

### Post by Skerit on 2008-04-24
I have the Antec Fusion V2 case, which DOES have an IR receiver (V1 didn't have one) It also has a VFD display and a wheel knob.

I've seen various posts where people are desperately trying to get their wheel knob to work and I'm surprised that I'm having the exact opposite problem over here. The wheel knob works fine, I can "record" it with ease, but the IR receiver does not.

I have the following files in /dev: lirc0 & lcd0 - but no other lirc file! 
I've already compiled the latest lirc from source but to no avail.

I'm trying this on a Gutsy machine, btw.

Thanks for your time.

---

### Post by Skerit on 2008-04-25
I recompiled lirc again, now with settings for the iMON ipad (or something)

When I execute the mode2 command I get feedback from the know just fine. I'm ALSO getting *a bit* of feedback from *a few* remote controls, from *a few* buttons. Yes, very strange! 2 remote controls out of the 4 have given me a small result, even though not all of these buttons work.

Is lirc ignoring those other buttons, because of the imon_ipad thing? Or is it something else I'm missing?

---

### Post by Skerit on 2008-04-25
Anyone, anything?

---

### Post by Monsieur Gonzalez on 2008-04-26
Hi!
I also have this case, and had a bit of trouble getting the IR remote to work. 

I'm using it with a Logitech Harmony remote, you don't mention which remote you're using (my case didn't come with one), and I got everything to work the way I want. 

Did you try irrecord to see if your remote gets detected? Are you using the Mythbuntu remote wizard?

I chose to do it using a custom remote file, and using it with the wizard.

I join the files I'm currently using, you might find them useful. Just remember my remote is a "learning" one, so the codes might not be the same.

Good luck, and I'll be glad to help, though I'm no expert ;)

Luis

ps. both hardware.conf and lircd.conf belong in /etc/lirc/

---

### Post by Skerit on 2008-05-13
I'm using any remote I can get my hands on! 
I'm not really using a specific one, I have one for the tv itself, for an old Hercules SmartTV card, my new Sat-S2 card, ... Some buttons make it react, most of them don't.

---

### Post by rhpot1991 on 2008-05-13
The receiver in the fusion can read MCE remotes.  Get one of those, activate imon_pad lirc module, irrecord your remote and then run mythbuntu-lircrc-genrerator on the resulting files.

You can find my config files here: [https://bugs.launchpad.net/mythbuntu/+bug/215960](https://bugs.launchpad.net/mythbuntu/+bug/215960)

---

### Post by Skerit on 2008-05-14
Hmmph, what a rip off! I didn't realise there were IR receivers who only work with MCE remoted. I can't believe it's *easyer* for the production process to limit an IR receiver like this! This is regular vendor-lock...

Anyhow, I'll try to make the IR port on my Technotrend S2-3200 work - but I'm stumped there, too! What driver do I use for it? 

Thank you for your time!

---

