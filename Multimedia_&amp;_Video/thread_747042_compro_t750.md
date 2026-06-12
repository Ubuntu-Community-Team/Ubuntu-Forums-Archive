---
title: "compro t750"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by louistan3 on 2008-04-06
Hey,

anyone here have any luck on getting this tv tuner to work? its a compro videomate t750..

i can see that ubuntu loads the saa7134 module but it still wont find any channels on mythtv..

i need help.....

---

### Post by kaivalagi on 2008-04-06
I have the same tuner card in my main PC and to be honest I don't really use it. I have a seperate media center PC with hauppague tuners instead.

I do know however that Hardy should be addressing the philips saa7134 chipset support. I have a hardy test partition which I updated yesterday, and the new kernel (2.6.24-15) has problems with the alsa sound portion of the chipset at the mo, it should be resolved soon....it is still in beta.

So.....if I were you  I'd wait and install the stable hardy release when it's available towards the end of the month. You may be in luck then.

Hope that helps

---

### Post by louistan3 on 2008-04-06
thanks kaivalagi..

so should i upgrade to hardy? cause this is on a running home server that is currently on feisty.. or can i just upgrade to a newer kernel?

anyone else have any info on support for this card?

thanks..

---

### Post by kaivalagi on 2008-04-06
I would guess you ought to upgrade to hardy for the new kernel version just to be safe, I'm not sure if theres an alternative that would work anyway.

I think you'd be best waiting until the end of the month (if you can) to see the outcome of hardy and this card compatibility.

If you search the forums for posts on "saa7134" you'll see a lot, and that means a lot of people can share their experiences, that should help to gauge things better. All the dectails for saa7134 should be applicable to your T750.

My experiences with saa7134 chipsets are minimal, as I have never attempted properly to get my T750 working in Linux...I just catch the odd mention here and there as I know I have that card and may need it working one day.

Do post back if you get anywhere, likewise if I find anything out on the hardy beta front I'll post the info.

Cheers

---

### Post by louistan3 on 2008-04-08
i am currently in the process of upgrading my server to hardy beta now..

i hope it works.. :)

---

### Post by kaivalagi on 2008-04-08
> **louistan3 said:**
> i am currently in the process of upgrading my server to hardy beta now..

i hope it works.. :)

Heads up, if you get a bunch of errors on boot up relating to saa7134 and audio, you need to blacklist the kernel module in some form of safe mode which gets you logged in.

```
gksudo gedit /etc/modprobe.d/blacklist
```


And add the relevant line at the bottom of the file to blacklist the module i.e.

```
blacklist saa7134
```

When you reboot all should be okay again, when a new kernel is released you may want to comment out the line again to see whether it works.

I will check these details more carefully when I get home, I'm at work (slack day) and have no access to a linux box to confirm any of this, all from memory

Edit: checked and alright

Cheers

---

### Post by louistan3 on 2008-04-10
well i cant seem to boot using the new kernel..

it mounts my filesystem as read only.. but using the older kernel works fine...

so now i cant test it yet.. im download some new updates now including a new kernel update.. i hope this one works.... 

thanks again for replyin kaivalagi.

---

