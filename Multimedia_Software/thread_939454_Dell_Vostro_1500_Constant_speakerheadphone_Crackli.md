---
title: "Dell Vostro 1500 Constant speaker/headphone Crackling even when EVERYTHING is muted!"
date: 2008-10-05
forum: Multimedia Software
---

### Post by minasmorath on 2008-10-05
Ok, I've been dealing with this problem for way to long: there is a constant crackling in my headphones and speakers (whichever one i'm using at the time). it isn't overly loud, but it's just loud enough to anno me. plus now i'm using this laptop as a recording studio, so it really stands out, because it shows up in all my recordings. I have a Dell Vostro 1500 laptop and the kernel is seeing my sound card as this:

```
mitchell@alexandria:~$ lspci
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

that appears to be right. as far as i can tell i am using the alsa sound system. side note: this didn't happen in M$ Vista before i wiped it - so i'm assuming it's an alsa issue.

If anyone has suggestions as to what i can try to get rid of this they would be greatly appreciated. oh, and as the title says, this seriously does happen when everything is muted.

Thanks Guys and Gals!

---

### Post by jpkotta on 2008-10-07
Are you sure that this didn't happen in Windows?  If it happens with everything muted, it really sounds like a hardware issue.  Does it still happen when you blacklist ALSA?  Or when you're in the BIOS?

```
sudo -i
echo blacklist snd >> /etc/modprobe.d/blacklist-alsa
exit

```

I have a Latitude D610.  The sound crackles, and it is definately a hardware issue.  I knew about this before buying it, and decided it was OK, and it usually is.  I bought a Turtle Beach USB sound card, for when I used the laptop as my main computer and the crackle was unacceptable.

---

### Post by ubergeek09 on 2009-03-19
Ok I had the same problem on a dell studio 1536. How I fixed it was I went into system>preferences>sound I then added the surround setting to the tracks that were controlled by my audio controls. Surround in my laptop for some odd reason controls the headphones and muting them along with everything else fixed the problem even though the headphone vooume was already cotrolled by the pcm track. hope this helps anyone.

---

