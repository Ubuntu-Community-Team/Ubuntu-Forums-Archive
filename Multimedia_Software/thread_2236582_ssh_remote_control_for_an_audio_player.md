---
title: "ssh remote control for an audio player"
date: 2014-07-27
forum: Multimedia Software
---

### Post by spacemen12 on 2014-07-27
I have a functional sound system with a source composed of a computer running 14.04 (Computer_A). I can do what I need with it:
- Play sound through the USB DAC
- Running Banshee or whatever player.

Now I want to be able to use a remote (computer computer_B) to control the Computer_A. There is an SSH server on Computer_A, I can ssh -X to Computer_A, open banshee (on Computer_A), but the music does not go anywhere (not in the built in speaker of computer_A, nor the USB DAC connected to it.) if I am not logged on Computer_A. If I am logged on Computer_A, the music goes to the built in speakers, even if in the same session I configure the sound output on Computer_A to be the USB DAC. 

How do I decide where to send the audio on Computer_A while I am controlling Computer_A from Computer_B (by SSH)?

Best regards,

---

### Post by tgalati4 on 2014-07-27
There are several ways to do this, but all require some configuration to get it to work the way you expect.

You could run *[mpd]("https://help.ubuntu.com/community/MPD")* (music player daemon) on your AV computer and then run one of several mpd clients on your remote computers.  Open a terminal:

```
apt-cache search mpd
```

Once you get that working, then you can try different methods for getting remote control playback:

moc via ssh
xbmc
rhythmbox with command-line control via ssh (rhythmbox --help-all)
banshee with command-line control via ssh  (banshee --help-all)

Put a RaspberryPi into the mix running Rune:  [http://www.runeaudio.com/](http://www.runeaudio.com/)

But I would start with *mpd* first and spend some time with it.

For your immediate issue, you might need the same user account on both machines (exact same username on both) to the the local USB DAC to work.  Try adding your username to group audio.

---

