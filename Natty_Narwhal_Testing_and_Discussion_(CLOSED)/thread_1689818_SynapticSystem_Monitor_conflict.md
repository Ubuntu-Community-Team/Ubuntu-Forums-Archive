---
title: "Synaptic/System Monitor conflict"
date: 2011-02-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-02-17
The System Monitor will not start if Synaptic is running. If you are running System Monitor, and then start Synaptic, System Monitor immediately crashes. Shutdown Synaptic, and System Monitor starts normally. Not an intermittent thing - 100% reproducible.

Does anyone else see this behavior?

---

### Post by dino99 on 2011-02-17
not with i386 here

---

### Post by ronacc on 2011-02-17
its ok here on amd64 (classic desktop no-effects) see SS, but as you can see in the screenshot system monitor does not show synaptic as running ?

---

### Post by sgage on 2011-02-17
> **dino99 said:**
> not with i386 here

Hmmm... happens here every time. I'm on i386 as well - Classic Desktop, no effects. I'm using the proprietary nvidia drivers, so I've held back the xserver updates - I wonder if that could have something to do with it...

---

### Post by Harry33 on 2011-02-17
> **sgage said:**
> Hmmm... happens here every time. I'm on i386 as well - Classic Desktop, no effects. I'm using the proprietary nvidia drivers, so I've held back the xserver updates - I wonder if that could have something to do with it...

Rigth now I can only test a Maverick setup (my girl friends pc) with xserver-xorg-ati-radeon and 64-bit architecture.
Started system monitor and then synaptic, everything runs just fine.
And they also should.

You can, however, test this:
open synaptic, the terminal and hit this:
```
sudo apt-get autoclean

```
And you get an error message:
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
But this is what should happen.

---

### Post by sgage on 2011-02-18
Here's what happens if I try to start System Monitor while Synaptic is running:

```
terminate called after throwing an instance of 'Gdk::PixbufError'
```

If I start Synaptic while System Monitor is already running, I get:

```
terminate called after throwing an instance of 'Gdk::PixbufError'
Aborted (core dumped)
```

Any ideas? Seems rather strange...

---

### Post by Harry33 on 2011-02-20
> **sgage said:**
> Here's what happens if I try to start System Monitor while Synaptic is running:

```
terminate called after throwing an instance of 'Gdk::PixbufError'
```

If I start Synaptic while System Monitor is already running, I get:

```
terminate called after throwing an instance of 'Gdk::PixbufError'
Aborted (core dumped)
```

Any ideas? Seems rather strange...

Is your system a fully upgraded/updated Natty-alfa2 i386?

---

### Post by sgage on 2011-02-20
> **Harry33 said:**
> Is your system a fully upgraded/updated Natty-alfa2 i386?

Yes. This problem occurs whether I use the nvidia drivers or nouveau.

---

### Post by Harry33 on 2011-02-20
> **sgage said:**
> Yes. This problem occurs whether I use the nvidia drivers or nouveau.

I tried several times either by starting Synaptic first and the System Monitor and the other way round.
But I could not reproduce any crash.
I am running otherwise fully upgraded/updated Natty alfa-2, but with xserver 1.9.2.
I use nvidia-current_270.26. 64-bit architecture.

---

### Post by sgage on 2011-02-20
> **Harry33 said:**
> I tried several times either by starting Synaptic first and the System Monitor and the other way round.
But I could not reproduce any crash.
I am running otherwise fully upgraded/updated Natty alfa-2, but with xserver 1.9.2.
I use nvidia-current_270.26. 64-bit architecture.

It seems like no one else has seen this, yet for me it is 100% reproducible. I am not going to worry about it - I have been hammering on this installation to the point where I have a number of minor glitches that I can't track down. 

Yes, time for a fresh install :KS

Thanks for looking into it, though.

---

