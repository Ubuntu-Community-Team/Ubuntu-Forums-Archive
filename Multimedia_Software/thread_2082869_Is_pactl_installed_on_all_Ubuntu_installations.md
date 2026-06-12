---
title: "Is pactl installed on all Ubuntu installations"
date: 2012-11-10
forum: Multimedia Software
---

### Post by ICouldBeAnyone on 2012-11-10
I have published an app to the software center called "Listen". It uses the command pactl to play bluetooth devices and microphones. I have had two bad reviews saying that it does not work. It works fine on both of my computers, both running Ubuntu 12.10 (ex 12.04 machines, it worked fine on 12.04 too).

So I have two questions, do all Ubuntu installations use PulseAudo, and do they also have pactl.

BTW: I am new to the forum and I couldn't think of a good user name. Did a post this in the correct place?

PS. The program is written in Mono C#

Please Help!  ](*,)

---

### Post by Cheesehead on 2012-11-10
Step 1: Find the full path for the pactl command.
```
$ which pactl
/usr/bin/pactl
```

Step 2: Detemine which package the command comes from.
```
$ dpkg -S /usr/bin/pactl
pulseaudio-utils: /usr/bin/pactl
```

Step 3: Work up the chain of dependencies until we find the *-desktop metapackges:
```
$ apt-cache rdepends pulseaudio-utils
pulseaudio-utils
Reverse Depends:
  [...]
  pulseaudio

$ apt-cache rdepends pulseaudio | grep desktop
  ubuntustudio-desktop
  ubuntu-desktop
  kubuntu-desktop

```

You can see that pactl is certainly installed with Ubuntu, Kubuntu, and Ubuntu Studio. You may need to bit more poking around to determine other flavors.

---

### Post by ICouldBeAnyone on 2012-11-10
Thanks for your help cheesehead.

That crosses that off the list for why it is not working. Ill have to do some more digging in google

Ill tell you more soon

---

