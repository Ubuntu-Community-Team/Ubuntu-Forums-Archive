---
title: "Cracking sounds and some applications not playing sound at all!"
date: 2011-06-11
forum: Multimedia Software
---

### Post by maverick280857 on 2011-06-11
Hi,

I am running Ubuntu Natty Narwhal 11.04 64-bit and Gnome 3 on my Dell XPS 15 laptop.

1. The default startup sound no longer plays.

2. Every time I start an application that accesses the sound card, I hear a cracking sound from the laptop speakers even when the headphones are plugged in.

3. Every now and then sound just stops playing. I am sometimes able to solve the problem using

```
pulseaudio -k
```

4. Skype startup sound and Thunderbird new mail notification sounds do not play, nor is any application other than VLC, Banshee, Rhythmbox, Movie player able to play any notification sounds. Empathy also can't play anything.

Any ideas where the problem could be?

---

### Post by G@Tenerife on 2011-06-15
Hi all,

I experience this missing sound issue the second time at Ubuntu 11.04 already, just without any cracking sound. I run the 32-bit edition. Installed 11.04 just a few days after it was released, and after the first update there were no

   1. startup sound,
   2. Skype sounds,
   3. Thunderbird sounds, new mail info exempted,
   4. Firefox sounds

anymore.

I tired to resolve this issue with Ubuntu Tweak's "Desktop Recovery" ... did not resolve, and thereafter re-started in my PC in recovery mode. No issue was detected at all. So I had to refurbish my PC in order to eliminate this issue.

After yesterday's update sadly I had to experience this issue again ... above listed sounds are gone again.

The biggest issue for me are the missing sound notifications of Skype, since it also does not give sound notification anymore when I receive an incoming call.

Did anyone else experience these missing sound issues?

Please reply with a re-solving solution as soon as possible. Having to refurbish the PC once a month is a little to much :(

Thank you all in advance for your help :)

---

### Post by G@Tenerife on 2011-06-16
Hi maverick280857,

I solved the issue :p!
I never experienced your cracking sound on 11.04 (it might be an x64 issue), but could recover all sounds again ...

Go to "Preferences" > "Sound" and adjust "Sound Effects" volume higher, and everything will work again as supposed to. I had to go all the way to 95 % to receive the same sound level as before the last update..

---

### Post by lidex on 2011-06-18
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by maverick280857 on 2011-06-20
> **G@Tenerife said:**
> Hi maverick280857,

I solved the issue :p!
I never experienced your cracking sound on 11.04 (it might be an x64 issue), but could recover all sounds again ...

Go to "Preferences" > "Sound" and adjust "Sound Effects" volume higher, and everything will work again as supposed to. I had to go all the way to 95 % to receive the same sound level as before the last update..

Yeah, this seems to have restored the startup sound, and the notification sounds. Thanks. But, I still have cracking sounds.

---

### Post by maverick280857 on 2011-07-01
Apart from Thunderbird still not playing a notification sound, everything else appears to have been resolved. I also reinstalled Natty, so :p

Marking this thread as solved.

---

### Post by lidex on 2011-07-02
> **maverick280857 said:**
> Apart from Thunderbird still not playing a notification sound, everything else appears to have been resolved. I also reinstalled Natty, so :p

Marking this thread as solved.

I'm assuming you have the notification sound enabled in 'edit > preferences > general'

---

