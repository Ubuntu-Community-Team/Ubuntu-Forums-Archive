---
title: "intermittent Mythtv tuner problem"
date: 2010-07-14
forum: Mythbuntu
---

### Post by adambh on 2010-07-14
Hi, am pulling my hair out trying to figure out what is wrong.

From a fresh set-up, mythtv works fine, then, usually after a few weeks, the tuner (generic "Wand TV HD USB DVB-T) stops working until I reinstall Mythbuntu. 

The error I get when tuning to Live TV is 
"() Signal 0% | BE 0 / S/N 2.1 dB |(|__) No Lock"

After attempting a channel change, I get 
"You should have received a channel lock by now. You can continue to wait for a signal or you can change the channel with Up or Down, change video source (Y), inputs (C), etc."

Recordings continue but record a black screen.

The tuner works when I try it with Windows on my laptop.

I'm not sure what the problem is, here are some things that may be wrong.
1) Poor tuner -signal not strong enough
2) Mythtv updates stuff the tuner driver
3) interference from somewhere (There's quite a lot of electronic equipment close to the tuner including the mythtv box, cd player, tv, digital set top box, cordless phone base, wireless router)
4) Signal too strong (I have the signal amplified)
5) Not enough RAM (only have 250MB)

If I can definitively diagnose the tuner as the problem, or the RAM, I will gladly spend money to fix it. However, I'm not so keen to throw away money chasing a diagnosis of the problem.

---

### Post by laffinet on 2010-07-14
Sorry I can't offer a solution, but at least a few comments for your dot points:
> 1) Poor tuner -signal not strong enough
When the tuner is working, what's your signal strenght and S/N ratio ?
> 2) Mythtv updates stuff the tuner driver
Unless you have enabled updates to install automatically (which I wouldn't recommend, and even then it should ask you for a password) mythbuntu/ubuntu doesn't just update stuff withou you knowing it. Did you run update manager and update any software ?
> 5) Not enough RAM (only have 250MB)
That does seem like a very small amout of RAM. Upgrade ?

---

### Post by LowSky on 2010-07-15
250MB of RAM? Did you mean 256 MB? Or are you confusing your terminology and meant a 250GB hard drive?

If it is 256 MB of RAM so that is quite low to run Mythbuntu and recording HDTV would be near impossible. Even a Windows PC couldn't record HD with that.

My first thought is that you set up Mythtv with the tuner and then things go well. Then at some point you remove the USB stick (because its a laptop and its mobile) and then try to plug it back in and it fails to work. The reason it fails is because the system gives it a new ID or a different serial port number when you replug it in. If you use a different USB port all toghter it will fail as well.

Also I have never heard of Wand TV HD USB DVB-T, it doens't appear in any of the MythTV documentation or on LinuxTV.org wiki either. with the card pluged in could you open a terminal and type ```
lsusb
``` (thats an d lower case L).. please post the out put here, it will give us the chip version and help us find info on the tuner

---

### Post by bance on 2010-07-15
I've had exactly the same problem.......... only for me it happens every other day. it turned out to be that the dish had moved.......... it has re-occurred , again today. But it has been quite stormy .so it could be the same thing. am going to check dish tomorrow.

I should say that I messed about with things the last few times and that really did for the set up.

I know that this is not a solution to your problem but it might help if it is as obviuos.

---

### Post by itlarson on 2010-07-16
This sounds a bit like the problem I had with a system using an Avermedia volar usb tuner.  It would work fine, untill it would suddenly stop working, with no signal strength.  I discovered that if I repeatedly plugged, and unplugged a flash drive my usb support completely crash, and I would loose my mouse and keyboard input.  I  disassembled and reassembled the computer and installed 32 bit mythbuntu instead of 64.  I also disabled legacy usb support in the bios.  It's been working for a week now,  I don't know if this is just luck, or if I fixed the problem.

---

### Post by adambh on 2010-07-20
[QUOTE=LowSky;9592713]250MB of RAM? Did you mean 256 MB? Or are you confusing your terminology and meant a 250GB hard drive?




256MB of RAM, which, like I said has worked in the past. Will get a 1GB stick off ebay. I think there may be a number of problems, as you've mentioned. 

1) unpluggin the stick from the usb port.
2) The signal may be too strong, as I've bypassed the amplifier now, and it seems to work again. Will post the outputs shortly.

---

