---
title: "Sound Recording"
date: 2008-01-26
forum: Multimedia Production
---

### Post by Master-of-None on 2008-01-26
Both Sound Recorder and Audacity freeze when I press their respective record buttons. Why?

---

### Post by erginemr on 2008-01-26
There should be a tool under Main Menu-> Preferences, called "multimedia systems selector" or similar. Does selecting "OSS - Open Sound System" for defaut input solve your problem?

You may also try selecting the record source from Audacity (Edit-> Preferences->Sound I/O) and Gnome mixer/sound setings.

---

### Post by Master-of-None on 2008-01-27
When I do that, it doesn't freeze, but it can't detect the type of stream

---

### Post by urangela on 2008-01-27
What is your sound card, and what system are you running?
Audacity would stop working for me if I had the wrong hardware interface selected ( I needed to switch from hw:1 to hw:0), The device selection is available from the prefferences menu. Also, how well are Alsa and Jack working for you?

---

### Post by Master-of-None on 2008-01-27
My card is: SB450 HDA Audio or so my hardrive info told me

ALSA also gives me the same error, or freezes the application.

I don't have JACK as an option when it comes to that.

---

### Post by Master-of-None on 2008-01-29
can someone help me out with this? If theres no way to fix it, I'd at least want to know that.

---

### Post by urangela on 2008-02-02
One thing you might try is downloading, and installing the[ ubuntustudio ]("http://ubuntustudio.org/")distribution, unless that is what you are using already. The next  thing to try is running A script that configures alsa called the configurator. It should be automatically installed with your system, check out this thread [here]("http://ubuntu.sabza.org/2007/05/07/troubleshooting-volume-and-sound-card-configuration-in-debian/")

---

