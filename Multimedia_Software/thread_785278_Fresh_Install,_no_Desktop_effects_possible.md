---
title: "Fresh Install, no Desktop effects possible"
date: 2008-05-07
forum: Multimedia Software
---

### Post by jcr1 on 2008-05-07
Hi all,

On a fresh install (+ then updated) of gutsy 7.10 I cannot enable desktop effects. I can only have it set to 'none'.

Any ideas why this is happening?...should I run a compiz-check script I have seen mentioned somewhere? Do I need fglrx installed? 

Spec in my sig.

---

### Post by Forlong on 2008-05-07
> **jcr1 said:**
> should I run a compiz-check script I have seen mentioned somewhere?
Yes, if it doesn't help you or you encounter any problems, post the output here.
> Do I need fglrx installed?
Not necessarily.

---

### Post by jcr1 on 2008-05-07
Aha! it was your script!!

Ran it and yup, got an error as suspected, hardware:

```
Gathering information about your system...

 Distribution:          Ubuntu 7.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz. 

Would you like to know more? (Y/n) y

 Your resolution is 1400x1050 but the maximum 3D texture size that your
 graphics card is cabable of is 1024x1024. Thus Compiz won't be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again). 


```

I understand what it is saying, but find it hard to accept i have to drop my resolution to use compiz-fusion... plus 1024 x 1024 is a bit odd...thats square!

---

### Post by Forlong on 2008-05-08
> **jcr1 said:**
> I understand what it is saying, but find it hard to accept i have to drop my resolution to use compiz-fusion...I'm afraid there's not much you can do about it.
After all it's just an old integrated graphics chip.
> **jcr1 said:**
> plus 1024 x 1024 is a bit odd...thats square!
That's the **maximum** resolution -- it doesn't mean you have to actually use that of course.
Anything below 1024x1024 will do the trick.

---

### Post by jcr1 on 2008-05-08
So are you basically saying if I set my resolution below 1024 x 1024 (say 1024 x 768 ) then I should be able to enable desktop effects?

Would this be the same case for running compiz-fusion?

That's a shame, I thought the graphics wasn't too bad on this laptop, hence the nice resolution. It ran 3D CAD programs ok...I don't think I could live with it in 1024 x 768, for too big, I like high resolution.

Thanks for your help.

---

### Post by bigken on 2008-05-08
have you installed the hardware drivers (restricted) in system administration

---

### Post by Forlong on 2008-05-08
> **jcr1 said:**
> So are you basically saying if I set my resolution below 1024 x 1024 (say 1024 x 768 ) then I should be able to enable desktop effects?
Yes.
> **jcr1 said:**
> Would this be the same case for running compiz-fusion?
"Desktop Effects" *are* Compiz (Fusion).
> **bigken said:**
> have you installed the hardware drivers (restricted) in system administration
It's not a driver but a hardware issue.

---

### Post by jcr1 on 2008-05-08
Ah man! I just went down to 1024 x 768 and got the effects working! I am really unhappy I can't have this in full res :(

Thanks for your help though :(

---

### Post by RJARRRPCGP on 2008-05-08
Shouldn't a Radeon 9000 be able to do 1152x864?



It probably can with Windows. 

I can't recall getting an error when running higher than 1024x768 under Windows.

---

### Post by Forlong on 2008-05-08
> **RJARRRPCGP said:**
> Shouldn't a Radeon 9000 be able to do 1152x864?
jcr1 is already running 1400x1050
> **RJARRRPCGP said:**
> It probably can with Windows. 

I can't recall getting an error when running higher than 1024x768 under Windows.
This is about running Compiz. I assume you didn't try to run Compiz on Windows either. ;)

---

### Post by Kaicias on 2008-12-17
I'm having a similar issue with a Radeon 7500 adapter, compiz:

 [COLOR="Blue"]Your resolution is 1400x1050 but the maximum 3D texture size that your
 graphics card is capable of is 1024x1024. Thus Compiz will not be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again). 
[/COLOR]
I cannot change the resolution using System/Preferences/Screen Resolution, can any one assist?

---

