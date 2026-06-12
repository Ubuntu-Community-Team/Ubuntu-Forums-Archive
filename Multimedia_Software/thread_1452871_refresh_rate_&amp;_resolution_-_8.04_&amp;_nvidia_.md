---
title: "refresh rate &amp; resolution - 8.04 &amp; nvidia card"
date: 2010-04-12
forum: Multimedia Software
---

### Post by soona86 on 2010-04-12
[FONT="Palatino Linotype"][SIZE="3"]Hi,

I use Ubuntu 8.04, My card is nvidia (GeForce I think) FX5200 & I'm on a desktop PC.
When I enable the card, the resolution doesn't work properly. The 1024 X 768 doesn't show 85 Hz.

I usually set it @ 1024 X 768 @ 85 Hz

But when I disable it, the resolution ( 1024 X 768 ) becomes available @ 85 Hz

So, What's with the whole refresh rate/resolution issue?[/SIZE][/FONT]

---

### Post by WinterRain on 2010-04-12
Do:
```
gksudo nvidia-settings
```
Then set your resolution and such, apply, then save to X configuration. This applies only if you are using the nvidia driver found in system>administration>hardware drivers.

---

### Post by soona86 on 2010-04-12
> **WinterRain said:**
> Do:
```
gksudo nvidia-settings
```
Then set your resolution and such, apply, then save to X configuration. This applies only if you are using the nvidia driver found in system>administration>hardware drivers.

Could you please explain that again. I'm still a beginner @ Ubuntu.
I opened the root terminal and typed that code and nothing happened.
Did I do something wrong here?
I enabled the driver btw

---

### Post by WinterRain on 2010-04-12
After you input those commands in the terminal, hit enter. Then it will ask for your password. Enter it, (but you won't see it on the screen) then hit enter again.

Btw, for long commands, you can copy and paste into the terminal to save time and avoid errors.

---

### Post by soona86 on 2010-04-13
> **WinterRain said:**
> After you input those commands in the terminal, hit enter. Then it will ask for your password. Enter it, (but you won't see it on the screen) then hit enter again.

Btw, for long commands, you can copy and paste into the terminal to save time and avoid errors.

I think I made a mistake I opened the root terminal..But I looked for another terminal & I found it..This one is called (Terminal) in (Accessories)

So, I typed the command; then Enter.
the password window appeared, I entered the password, then Enter
then nothing happened

I understand it's case sensitive. I typed it just as you sent it here

I hope I'm not bothering you :oops::oops::oops:

Thanks :)

---

