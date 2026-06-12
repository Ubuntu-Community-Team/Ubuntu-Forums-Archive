---
title: "Sony Bravia 32&quot; LED probs with resolution and display settings"
date: 2012-11-11
forum: Multimedia Software
---

### Post by Kestrel78 on 2012-11-11
I've recently attached a Sony Bravia 32" LED display to my Ubuntu 12.04 system.  Previously I'd had a square 19" LCD attached.  For some reason I can't get it to a wide-screen aspect, rather than the old-school square one.  When I go to displays it seems to want to stick with 'laptop.'  Detect displays doesn't seem to do much either.  Suggestions?

---

### Post by dannyboy79 on 2012-11-11
what is the output of this command entered into a terminal?

```
sudo lspci | grep VGA
```

for example, my output is this:
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

just need to see what sort of graphics card you have

---

### Post by Kestrel78 on 2012-11-11
04:00.0 VGA compatible controller: NVIDIA Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by dannyboy79 on 2012-11-12
ok, good so far. now enter this to see which driver you're using
```
dmesg | grep NVIDIA
```

---

### Post by Kestrel78 on 2012-11-12
[   24.926026] nvidia: module license 'NVIDIA' taints kernel.
[   25.846051] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.35  Thu May 31 12:00:16 PDT 2012

---

### Post by Kestrel78 on 2012-11-12
Found this thread from a fellow who appears to have had the same problem a few months back.  

[http://ubuntuforums.org/showthread.php?t=2039307](http://ubuntuforums.org/showthread.php?t=2039307)

I'll do a full shut-down and disconnect on my computer while I'm out at work today, then see how things are doing this evening.  Maybe the same 'magical' reset will take place :-P

---

### Post by Kestrel78 on 2012-11-12
And no luck when I reconnected everything this evening :/

---

### Post by papibe on 2012-11-12
It looks you are using the Nvidia proprietary driver.

If so, don't use 'Monitors' but 'Nvidia X Server Settings' instead. Configure the resolution you need and then save your setting by pressing 'Save to X configuration file'.

Let us know how it goes.
Regards.

---

### Post by Kestrel78 on 2012-11-12
I opened the Nvidia x server settings, went to Display Configuration and found the layout as 'Sony TV (Disabled)', Model drop-down was listed as 'SONY TV (CRT-1 on GPU-0)', and configuration drop-down listed as disabled.  Detect Displays didn't do anything.  I changed the configuration drop-down to 'Separate X Screen (requires restart) and that brought up 'SONY TV 1360x 786' on the layout thumbnail.  Saved changes to X configuration file, quit, restarted. . . and no change, and the Nvidia X Server settings were back to what they were before I'd opened them.

Does it matter that I'm hooked up by VGA?  Might an HDMI connect help things along?

---

### Post by papibe on 2012-11-12
Try again, but this time run it as administrator:
```
gksudo nvidia-settings
```

> **Kestrel78 said:**
> Does it matter that I'm hooked up by VGA?  Might an HDMI connect help things along?

You would have both a better signal, and more chances of reading the correct TV EDID information using a pure digital connection. That is, a pure HDMI cable or a DVI-to-HDMI cable.

---

### Post by Kestrel78 on 2012-11-12
Did as you said, and same result as before :( Layout shows 'SONY TV (Disabled) and configuration drop-down is Disabled.

---

### Post by papibe on 2012-11-12
Is the TV turned on when you boot?

---

### Post by Kestrel78 on 2012-11-12
It is.

---

