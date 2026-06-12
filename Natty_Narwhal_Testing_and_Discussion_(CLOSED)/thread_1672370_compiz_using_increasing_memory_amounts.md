---
title: "compiz using increasing memory amounts"
date: 2011-01-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mc4man on 2011-01-20
Previous to today I'd noticed compiz leaking (if that's an appropriate term?) a small amount during use.
After the current updates it seems to have taken off quite a bit, I think from opening and clicking on icons the new places thing 

Using pidstat to record as in 
 ps -A  |grep compiz
then using the pid in (replacing XXXX w/ pid found
```
pidstat -r -p XXXX 60 100 >> mem.log
```
Ex. over a few min. - small increases are normal activities, large are from the dash or whatever it's called, none are from no activity
```
linux 2.6.37-12-generic (doug-alienware) 	01/20/2011 	_i686_	(2 CPU)

07:33:48 PM       PID  minflt/s  majflt/s     VSZ    RSS   %MEM  Command
07:34:48 PM      1290      1.67      0.00  218424 109208  10.66  compiz
07:35:48 PM      1290      0.00      0.00  218424 109208  10.66  compiz
07:36:48 PM      1290      0.00      0.00  218424 109208  10.66  compiz
07:37:48 PM      1290      0.00      0.00  218424 109208  10.66  compiz
07:38:48 PM      1290      0.00      0.00  218424 109208  10.66  compiz
07:39:48 PM      1290    203.92      0.00  261940 139492  13.61  compiz
07:40:48 PM      1290    467.32      0.00  339624 219472  21.42  compiz
07:41:48 PM      1290     43.32      0.00  336884 220160  21.49  compiz
07:42:48 PM      1290     27.30      0.00  342416 220204  21.49  compiz
07:43:48 PM      1290    195.57      0.00  364488 246608  24.07  compiz
07:44:48 PM      1290      5.18      0.00  364068 247064  24.11  compiz
07:45:48 PM      1290      6.78      0.00  363616 245860  24.00  compiz
07:46:48 PM      1290      5.40      0.00  363928 246048  24.02  compiz
07:47:48 PM      1290    154.13      0.00  389696 271856  26.53  compiz
07:48:48 PM      1290      9.08      0.00  391232 272176  26.57  compiz
07:49:48 PM      1290      5.08      0.00  391232 272416  26.59  compiz
07:50:48 PM      1290    152.78      0.00  422160 298572  29.14  compiz
```
above is 1 gig mem machine (p4 - below from a 3 gig, about the same -  %'s are obviously lower
```
Linux 2.6.37-12-generic (doug-XPS-M1330) 	01/20/2011 	_i686_	(2 CPU)

07:30:39 PM       PID  minflt/s  majflt/s     VSZ    RSS   %MEM  Command
07:31:39 PM      1357      2.12      0.00  188536  97376   3.15  compiz
07:32:39 PM      1357      0.00      0.00  188536  97376   3.15  compiz
07:33:39 PM      1357      1.55      0.00  189764  97684   3.16  compiz
07:34:39 PM      1357     12.95      0.00  193720  98828   3.19  compiz
07:35:39 PM      1357    229.67      0.00  225816 132184   4.27  compiz
07:36:39 PM      1357     21.95      0.00  225964 133508   4.31  compiz
07:37:39 PM      1357    106.75      0.00  241736 146956   4.75  compiz
07:38:39 PM      1357     92.42      0.00  253256 160072   5.17  compiz
07:39:39 PM      1357      2.98      0.00  253256 160276   5.18  compiz
07:40:39 PM      1357      0.00      0.00  253256 160276   5.18  compiz
07:41:39 PM      1357      0.02      0.00  253256 160276   5.18  compiz
07:42:39 PM      1357      0.00      0.00  253256 160276   5.18  compiz
07:43:39 PM      1357      0.02      0.00  253256 160276   5.18  compiz
07:44:39 PM      1357    146.63      0.00  281584 186100   6.01  compiz
07:45:39 PM      1357      4.62      0.00  279068 185996   6.01  compiz
07:46:39 PM      1357      0.02      0.00  279068 185996   6.01  compiz
07:47:39 PM      1357      0.00      0.00  279068 185996   6.01  compiz
07:48:39 PM      1357      0.00      0.00  279068 185996   6.01  compiz
07:49:39 PM      1357      0.00      0.00  279068 185996   6.01  compiz
07:50:39 PM      1357      0.00      0.00  279068 185996   6.01  compiz
07:51:39 PM      1357      0.00      0.00  279068 185996   6.01  compiz
07:52:39 PM      1357     60.90      0.00  296588 198432   6.41  compiz
07:53:39 PM      1357     84.33      0.00  308152 211648   6.84  compiz
07:54:39 PM      1357      0.15      0.00  308152 211648   6.84  compiz
07:55:39 PM      1357      0.02      0.00  308152 211648   6.84  compiz
07:56:39 PM      1357      0.07      0.00  308152 211648   6.84  compiz
07:57:39 PM      1357      0.00      0.00  308152 211648   6.84  compiz
07:58:39 PM      1357      0.05      0.00  308152 211648   6.84  compiz
07:59:39 PM      1357      4.47      0.00  305044 211828   6.85  compiz
08:00:39 PM      1357     39.43      0.00  309980 213648   6.90  compiz
08:01:39 PM      1357      0.75      0.00  305124 213640   6.90  compiz
08:02:39 PM      1357    144.82      0.00  332692 239768   7.75  compiz
08:03:39 PM      1357     43.18      0.00  339948 241332   7.80  compiz
08:04:39 PM      1357      8.38      0.00  340132 241540   7.81  compiz
```

---

### Post by ratcheer on 2011-01-20
Yep, compiz is using about 25% of my RAM, right now. Thanks for pointing this out.

Tim

---

### Post by Quackers on 2011-01-20
I've only had my box on for 3 hours or so. Compiz is using about 2.7MB more than it was before. I'll keep an eye on it though.

---

### Post by kyleabaker on 2011-01-20
I was just about to start a thread about this. Compiz usually runs around ~90mb for me, which I still think is too much. After each time I open the Dash view it adds ~25mb, so in playing around and checking the new icons it went up to around ~600mb.

I seem to constantly be killing compiz and restarting it (from my desktop bash file) to free up wasted ram.

---

### Post by Quackers on 2011-01-20
Wow, that's a serious leak! Compiz seems to run at about 129MB of ram for me (but I like the spangly bits :-) ). It's now at 136MB, so it's jumped a bit from a few minutes ago.

---

### Post by Ellipsis on 2011-01-20
> **kyleabaker said:**
> I was just about to start a thread about this. Compiz usually runs around ~90mb for me, which I still think is too much. After each time I open the Dash view it adds ~25mb, so in playing around and checking the new icons it went up to around ~600mb.

I seem to constantly be killing compiz and restarting it (from my desktop bash file) to free up wasted ram.

RAM is never wasted: it is used. :)

Using 100mb of RAM on a decently spec'd machine will make little difference unless you are consistently using huge memory amounts (90%+). Even when using 600mb compiz is using that space for a reason: it is available. It would be unacceptable if Compiz was using this space when it was required by other applications and creating a drop in responsiveness/performance of those applications. 

Of course there issues with using RAM unnecessarily but when it is necessary  for user experience it should be used. After all that is why we are not using it. In an ideal world a machine should use 100% of your RAM but instantly free up RAM for other applications when it was needed. 

Sorry for going on for a while but I always feel the need to explain this when ever RAM is brought up. This specific issue of 600mb usage and memory leaking is likely a bug. :)

---

### Post by kyleabaker on 2011-01-20
> **Ellipsis said:**
> Sorry for going on for a while but I always feel the need to explain this when ever RAM is brought up.

I think we all understand what ram is for. The problem here is a leak, but applications should be working more efficiently and using more ram just cause its there isn't exactly efficient or good practice.

> **Ellipsis said:**
> This specific issue of 600mb usage and memory leaking is likely a bug. :)

Its without a doubt a bug, and I'm sure the leak will be plugged soon.

---

### Post by ronacc on 2011-01-20
my box has been up about 4 hrs using classic desktop and compiz is only showing 12.8 MB used in system-monitor and 0.7% in htop . my sys is amd64 with 4gb mem nvidia 7600gs and nvidia-current driver .

---

### Post by mc4man on 2011-01-21
> using classic desktop and compiz is only showing 12.8 MB...
This is all on the unity end, classic is quite fine here also. (A hair higher here but quite steady thru use.
Typically here before today compiz used about 2.5 times more at login to unity than to classic though overall the amount for either is/was insignificant 

The update today, issues aside, did increase the amount at login by about 40%,  50 > 70 MB on a laptop, slightly higher values on desktop, though again those initial amounts don't particularly matter   much

---

### Post by ratcheer on 2011-01-21
When I replied last night, my Compiz with Unity was using 242 MiB. When I switched to Classic, Compiz was using 23 Mib. Right now, after more library updates that came this morning, Compiz with Unity is using 190 Mib and that is increasing.

This is way too much memory usage, but I realize we are in Alpha.

Tim

---

### Post by anders_c_ on 2011-01-21
Opening and closing dash adds another 25M to compiz, currently at 1.5G. It doesn't seem to leak if i don't touch dash though.

---

### Post by ratcheer on 2011-01-21
> **anders_c_ said:**
> Opening and closing dash adds another 25M to compiz, currently at 1.5G. It doesn't seem to leak if i don't touch dash though.

I have only heard the term twice and I have no idea what it refers to. What is dash?

Thanks,
Tim

---

### Post by mc4man on 2011-01-21
I've seen it move up slowly over time thru general use or a bit more when something else goes south, typically menu related (other than dash

Anyway here's one bug report if wished to comment on or confirm
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/705705](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/705705)

---

### Post by dino99 on 2011-01-21
only for the lazy

[http://packages.ubuntu.com/natty/dash](http://packages.ubuntu.com/natty/dash)

---

### Post by anders_c_ on 2011-01-21
> **ratcheer said:**
> I have only heard the term twice and I have no idea what it refers to. What is dash?

Thanks,
Tim
The unity menu. 
Not the debian almquist shell!

---

### Post by ratcheer on 2011-01-21
> **anders_c_ said:**
> The unity menu. 
Not the debian almquist shell!

The Unity menu? Unity doesn't have a menu. That is one of the things I don't like about it.

dino tells me its the Debian Almquist shell and anders tells me its not. More confusion....

Tim

---

### Post by anders_c_ on 2011-01-21
The unity menu showed up a few hours ago for me, might be different depending on what update server you are using. And Canonical has chosen to call it "dash" which is also the name of the debian almquist shell. In my post i only meant the unity dash and I'm pretty sure the other guy who mentioned dash in this thread was referring to the same thing.

Here's a little article about the first version of dash:
[http://www.omgubuntu.co.uk/2011/01/unity-update-brings-the-dash-or-part-of-it-at-least/]("http://www.omgubuntu.co.uk/2011/01/unity-update-brings-the-dash-or-part-of-it-at-least/")

---

### Post by ratcheer on 2011-01-21
> **anders_c_ said:**
> The unity menu showed up a few hours ago for me, might be different depending on what update server you are using. And Canonical has chosen to call it "dash" which is also the name of the debian almquist shell. In my post i only meant the unity dash and I'm pretty sure the other guy who mentioned dash in this thread was referring to the same thing.

Here's a little article about the first version of dash:
[http://www.omgubuntu.co.uk/2011/01/unity-update-brings-the-dash-or-part-of-it-at-least/](http://www.omgubuntu.co.uk/2011/01/unity-update-brings-the-dash-or-part-of-it-at-least/)

Thank you.

Tim

---

### Post by mc4man on 2011-01-21
I used dash intending places not a shell

---

### Post by ronacc on 2011-01-21
I think they called it dash as a short form of "dashboard" . if they intended it as an imitation of Apple's dashboard they missed the mark .

---

