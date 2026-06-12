---
title: "Xorg in 9.04 causes high cpu load in idle state"
date: 2009-06-25
forum: Multimedia Software
---

### Post by digitoxin on 2009-06-25
Hello!

On all PCs where i installed ubuntu 9.04 xorg load is superhigh.

This is independent of hardware, i noticed that on totally different PCs.

Here is a sample of top output:
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2852 root      20   0  396m  71m 5032 R 29.1  7.2  77:35.80 Xorg

Thats 29,1% CPU load in idle state, and that on every PC i installed ubuntu 9.04
No program is running or anything else that causes cpu load. Also, i installed the old intel driver on PCs with intel card and things go a little faster, still nothing changed about the cpu load.

---

### Post by madverb on 2009-06-25
Are all of these PC's identical?

---

### Post by lovinglinux on 2009-06-25
I think the real problem is not xorg, but vino-server, which loads at boot by default. It seems that there is a bug in the "Remote Desktop" server in Jaunty. Go to "System >> Preferences >> Startup Applications" and disable "Remote Desktop" then reboot. 

Also try to perform an update. The recent xorg, compiz and kernel updates reduced CPU usage considerable on my machine.

Did you installed any application dependent on Python 2.5? If yes, then it might be the culprit. Python 2.5 is definitely not playing well in Jaunty. 

Check some possible tweaks at [http://ubuntuforums.org/showthread.php?t=1152095](http://ubuntuforums.org/showthread.php?t=1152095)

---

### Post by digitoxin on 2009-06-25
Hmm i think vino-server is not running. ps aux |grep vino does not find anything...
Also, compiz is not running, i always turn it off..
And also software is the latest.

And this effect does not depend on hardware or is difficult to reproduce. Its installing, making a console window, typing top, watching the result and beeing horrified. Nothing more needed.

Well so far my advice is staying with 8.10 if you don't want to end up with noisy laptop fans and degraded performance.....

---

### Post by digitoxin on 2009-06-25
It seems its not just the idle state, total cpu load has increased dramatically in 9.04.

Now playing a mp3 in audacious uses 50% (30% xorg, 20% audacious) cpu load, the same thing in 8.10 only used 5%

So there seems to be a general problem with X performance in 9.04 :(

---

### Post by madverb on 2009-06-25
I don't believe this is occuring on multiple machines. Considering I have installed 9.04 on quite a few machines and haven't had any of the problems you are suggesting. Maybe a minor increase in CPU and Memory usage but not really noticeable.

---

### Post by digitoxin on 2009-06-26
Maybe on faster PCs it does not show that strong. The numbers i posted are the ones i got on a 1Ghz Pentium M. Equal numbers i also get on my Netbook with Intel Atom processor.

Fact is notebook fans are much louder with 9.04 and battery runtime is quite reduced...

---

### Post by Kismet on 2009-07-07
Maybe this should be filed/appended to a bug report, As I too can verify excessive Xorg cpu usage on multiple machines, seemingly independent of hardware.

On this machine right now, my Xorg is sitting at about 10% as I type this.

If I do something like run peacekeeper (futuremark.com/peacekeeper). Top shows ~ 80% usage firefox, ~ 80% usage Xorg (It's a dual core). So it would appear that drawing to the screen is very slow. It's also noticable when I switch desktops. 
It acts like its swapping even though I have 4G of ram, and only using about 2 of them.

---

### Post by NaseEder on 2009-07-22
I can confirm that disabling "remote desktop" dropped cpu-usage
from 30-40%@1.8GHz
to 10-12%@1GHz

having firefox open and Audacious playing an online-stream, this is cpu-load as i would expect..
'top' shows xorg idling at max 4% where it was at max 30% before.

system is:
X2@2.8GHz
Ubuntu 9.04

solved for me.

---

### Post by t4thfavor on 2009-07-23
I just got hit by this after I reconfigured my Xsettings for three monitors (unsuccessfully). When I reverted back, I had 70-80% cpu. 


I then stopped vino-server, and waited a bit, now my cpu idles properly again...

I am just wondering why this never bothered me before, and all I did was change xorg files, and then revert back.

---

### Post by craig_ on 2009-09-01
9.04 // x64 // HP nx6325 laptop.

I had the same problem. Removing vino-server (Remote Desktop) from startup caused CPU load when idle to be (virtually) nil.

However, as i rely on remoting to this machine, i created a script which has the following in it and ran it at startup instead. Once it executes, it does not cause the extra load. I dont know why it works, but it did for me.

```
sleep 10 && /usr/lib/vino/vino-server
```

---

### Post by Pagamim on 2009-09-06
yes, i have the same problem, whenever i start remote desktop server the CPU usage goes up to 100% with "vino-server" but when i disable the remote desktop server off everything goes back to normal :S its strange because never of this happed before only now.

any ideias?

thanks

---

### Post by lovinglinux on 2009-09-06
> **craig_ said:**
> However, as i rely on remoting to this machine, i created a script which has the following in it and ran it at startup instead. Once it executes, it does not cause the extra load. I dont know why it works, but it did for me.

I recommend using ssh instead of remote desktop, for security reasons. If you really need vino-server, you can connect to the server via ssh, start the vino-server remotely when you need and then tunnel the remote desktop connection via ssh. This is much more secure.

---

### Post by Pagamim on 2009-09-06
i solved my problem :S strange but it did work lol xD

all i did to stop the high cpu usage was remove the vino-server from starting aplications and rebooted, and that did the job :S

later i went to remote desktop server and turned it on, and its working 100% with normal cpu usage.

whats the diference having vino-server as a starting aplication if it is still enable after reboot ? 

thanks

---

### Post by lovinglinux on 2009-09-06
> **Pagamim said:**
> whats the diference having vino-server as a starting aplication if it is still enable after reboot ? 

Go to Startup Applications and disable it there, otherwise it will start again after reboot.

---

### Post by Pagamim on 2009-09-06
> **lovinglinux said:**
> Go to Startup Applications and disable it there, otherwise it will start again after reboot.

sorry, maybe i have explained myself wrong, i had the remote desktop server on, and starting on the boot, but for no reasson at a point the CPU usage started to go high, and all i did to solve this was ONLY remove it from starting aplications and all went back to normal, i can still use the remote desktop server even if i dont have it on the starting aplications.

thanks

---

### Post by photoscotty on 2009-09-07
I'm having the same issues on a fresh install of Ubuntu Studio Jaunty.

I'm running a Vostro 1000 (Athlon64 X2 1.8Ghz, 4GB Ram) and my idle CPU usage runs around 50-55%.

I tried the remote desktop suggestion, but so far I'm not seeing any change.

Not sure if this is common to rest of you in this thread, but none of my idle processes use over 3%, but yet the 50% being reported.

---

### Post by lovinglinux on 2009-09-07
> **photoscotty said:**
> I'm having the same issues on a fresh install of Ubuntu Studio Jaunty.

I'm running a Vostro 1000 (Athlon64 X2 1.8Ghz, 4GB Ram) and my idle CPU usage runs around 50-55%.

I tried the remote desktop suggestion, but so far I'm not seeing any change.

Not sure if this is common to rest of you in this thread, but none of my idle processes use over 3%, but yet the 50% being reported.

I have already replied to you in the other thread.

---

### Post by rod40cool on 2009-09-19
Thanks lovinglinux. I can confirm that disabling remote desktop brought my idle CPU usage way down from 50-70% to a more respectable level.

---

### Post by herdivet on 2009-11-21
I had this problem as well, but really wanted to have RDP available.  I found that by taking 'Remote Desktop' out of the Startup Applications and then choosing Remote Desktop from the Preferred Applications and it now runs without pegging the CPU and starts automatically on reboot.

Your mileage may vary.

Bill

---

