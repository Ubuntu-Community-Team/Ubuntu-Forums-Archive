---
title: "No sound recording in Feisty"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by martijn_bakker on 2007-05-07
After installing Feisty, I had some problems with getting my sound to work. This was probably due to the facts that:
1. My system recognises three sound cards and could not determine which one to use by default.

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
01:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:07.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)

2. The output of the Audigy was set to the digital interface by default.

1. was solved using asoundconfig.
2. was solved using alsamixer

So, now I have sound output. I can even get sound from my microphone back via the speakers, so I know the microphone and mixer settings work.

However, I can not record sound from any source at all. Do any of you have a suggestion?

---

### Post by ericdegen on 2007-05-08
I'm getting the same thing on my HP NC8430 notebook - output great, but no mic in.

---

### Post by Gibran on 2007-05-09
Exact same problem here, too...Anyone??

---

### Post by ericdegen on 2007-05-09
Little more info on this.

I have two systems both with 7.04 installed at the same time, the desktop using an AC97 chipset works fine (the record functions and playback) but on the notebook with a SoundMAX HD - no love.

---

### Post by hallbuzz on 2007-05-11
> **ericdegen said:**
> I'm getting the same thing on my HP NC8430 notebook - output great, but no mic in.

Me too using HP pc with either Dapper or Feisty

---

### Post by detyabozhye on 2007-05-19
Same here: SB Audigy 2

---

### Post by detyabozhye on 2007-05-19
Figured it out: in alsamixer (command line), go to capture, press sapce under Master (so that it will have red text under it), same with Mic, turn Mic up to ~80, then turn up Analog mix up to 100. That fixed it for me.

---

### Post by ericdegen on 2007-05-19
I was finally able to get mine working on the HP NC8430 with some help from this thread [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/4912](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/4912).

After adding the line "options snd-hda-intel model=ref position_fix=0" to /etc/modprobe.d/alsa-base, rebooting and then selecting the OSS device inside skype - I was finally running.

Hope that helps someone.

---

### Post by euchrid on 2007-06-07
I had to update the Alsa drivers (from 1.0.13 to 1.0.14). Nothing else worked for me. I put all the information about it here: [http://ubuntuforums.org/showthread.php?p=2798055#post2798055]("http://ubuntuforums.org/showthread.php?p=2798055#post2798055")

Hope it's useful to someone.

---

