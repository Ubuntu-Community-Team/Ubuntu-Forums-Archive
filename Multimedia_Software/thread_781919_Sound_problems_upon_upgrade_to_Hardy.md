---
title: "Sound problems upon upgrade to Hardy"
date: 2008-05-04
forum: Multimedia Software
---

### Post by WizardMagus on 2008-05-04
Hello.  I have an HP Pavilion dv6000, and I just upgraded from Gutsy to Hardy.  Since this time I have been having weird sound problems.  The sound is incredibly scratchy, or sounds like it has very high bass, if that makes sense.

I get the same problems no matter what file type I play, if I play something online, etc.  I tried using headphones and the laptop speakers and both have the same problem.  I also tried changing devices, and Alsa, OSS and PulseAudio all have a similar problem.

This is my lspci output:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Does anyone know what the problem might be?  Let me know if I need to provide additional information.  Thanks for the help!

---

### Post by WizardMagus on 2008-05-06
Anyone?  My sound is unusable.

---

### Post by nickko on 2008-05-07
There seems to be lots of issues with pulseaudio soundserver. Try to kill pulseaudio process through the system monitor.

If that solves the problem, i described a way to disable pulsaudio on startup (it is impossible to totally remove it without removing kubuntu desktop on hardy) on the "how to disable pulsaudio" thread

---

### Post by WizardMagus on 2008-05-07
> **nickko said:**
> There seems to be lots of issues with pulseaudio soundserver. Try to kill pulseaudio process through the system monitor.

If that solves the problem, i described a way to disable pulsaudio on startup (it is impossible to totally remove it without removing kubuntu desktop on hardy) on the "how to disable pulsaudio" thread

I killed the pulseaudio application but the problem continues.  Any more thoughts?

---

### Post by selda on 2008-05-07
I had lots of sound problems lately. Killing pulsaoudio solved all problems. Thanks for the hint.

---

### Post by Gromwalh on 2008-05-10
I'm having the same problem on the same laptop.  Just tried killing pulseaudio and problem remains.  Worked great under 7.10.  Any ideas would be appreciated.  Thanks!

---

### Post by Zorael on 2008-05-10
Many have issues with Intel HDA-related soundcards, and there are easy fixes for some of us lucky ones.

See [http://ubuntuforums.org/showpost.php?p=4869649](http://ubuntuforums.org/showpost.php?p=4869649) as well as the post I linked to there.

Failing that, you may have to compile the [FONT="Courier New"]snd_hda_intel[/FONT] module from a newer source. Or an older one, seeing as it worked for mostly everyone in 7.10.

More info over at [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel).

---

### Post by Gromwalh on 2008-05-10
I just came across [this]("http://ubuntuforums.org/showpost.php?p=4274857&postcount=19").  I don't know why it worked, but it did the trick for me.  Good luck!

---

### Post by WizardMagus on 2008-05-11
> **Gromwalh said:**
> I just came across [this]("http://ubuntuforums.org/showpost.php?p=4274857&postcount=19").  I don't know why it worked, but it did the trick for me.  Good luck!

This worked!  Thank you for the help.

---

