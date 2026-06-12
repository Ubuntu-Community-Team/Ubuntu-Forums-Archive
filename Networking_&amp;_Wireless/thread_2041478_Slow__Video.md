---
title: "Slow  Video"
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by Ertai87 on 2012-08-12
Not sure exactly what the issue is here; whether it's my computer, Ubuntu, Firefox, Flash, etc, but I seem to have trouble streaming video.  I thought the issue was the streaming service, but I've been trying to watch videos on YouTube and having problems there as well.  The issue is just that all the videos are very slow and choppy.  I've tried checking System Monitor while watching a video and it doesn't seem like I'm using a lot of RAM or a lot of network resources at all, but the video is just very slow and choppy when it shouldn't be.  Does anyone have any suggestions?  Thanks.

---

### Post by bakegoodz on 2012-08-12
Is the computer using wireless? If so paste the output of:
```
iwconfig
```

---

### Post by irv on 2012-08-12
also if you are using wireless, try resetting your router. I had trouble one night and just resetting the router fix it. Just a thought. Also do a test on your Internet speed. I use [http://www.speakeasy.net/speedtest/]("http://www.speakeasy.net/speedtest/")
[ATTACH]222626[/ATTACH]

---

### Post by johnathansmith on 2012-08-12
Could you try from 240p to 1080p quality video, if they both chopped?

---

### Post by Ertai87 on 2012-08-12
> **bakegoodz said:**
> Is the computer using wireless? If so paste the output of:
```
iwconfig
```

```
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:[REDACTED]  
          Mode:Managed  Frequency:2.437 GHz  Access Point: [REDACTED]   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4107  Invalid misc:24421   Missed beacon:0

eth0      no wireless extensions.
```

Removed the parts that might identify my personal identity, but otherwise there you have it.

---

### Post by bakegoodz on 2012-08-13
It appears your Wi-Fi link is great.

---

### Post by irv on 2012-08-13
You won't believe this but I was just getting ready to ask if you restarted your router when I stated having trouble with everything slowing down. I went and restarted my router and everything is back working again. So the question is, did your try restarting your router?

---

### Post by Ertai87 on 2012-08-13
Last night I was watching a video I was previously having a lot of difficulty with, and the stream appeared to be a lot smoother than usual; it was still somewhat choppy, but it was at least watchable (while it usually isn't).  I didn't change anything in my configuration before then, so I don't know what changed.

I restart my router occasionally, but I don't notice a significant change in this issue when I do.  Next time there's a video I want to watch that's choppy I can try it, but I doubt that's the issue.  Additionally, the other people on my network (who use Windows) don't seem to have the same issue, and when I watch a video on my iPod Touch I also don't experience the same issue; the issue appears to be exclusively on my Ubuntu computer.

---

### Post by irv on 2012-08-13
Another thing to check is what is running in the background. Before and while you are watching a video run this command in a terminal.
```
top
```
This will monitor apps and services running on your computer. It will show CPU usage and memory used and also swap drive used.
I guess no one asked if you have a swap setup and what size? You can post a screen shot of the terminal when top is running.

---

### Post by Ertai87 on 2012-08-13
I can check that next time I'm watching a bad video, but I checked System Monitor last time; both RAM and Network were at about 60% usage according to System Monitor, although when the video chopped up the netowrk usage dropped to 0.

---

### Post by Ertai87 on 2012-08-22
Watching a really choppy video of my friend livestreaming something right now.  Here's a screenshot of a terminal running top so you can dissect the data.

EDIT: I also just tried using Google Chrome to watch the video.  In Firefox I'm getting about 1.5 real-time seconds to 1 video second; in Chrome I get about 2 video seconds per real-time second; it's the opposite problem.  I think my video plugin is borked, but I have no idea how to fix it.

EDIT2: Uninstalled and reinstalled Flash from Software Center and rebooted the computer.  Now it seems to work.  Don't know if it was Flash or if it was rebooting the computer.  If anyone sees anything fishy in my top result though, let me know.

---

### Post by irv on 2012-08-23
You posted this a week ago. Is this the first time you tried rebooting? Anytime I have a slow down the first thing I do is try a fresh power down restart, this clears all memory.

Yes I see from your screen shot that you have plugins running in your browser which are taking up most of the memory. This will slow things down.

Also you do not have much memory to begin with. My laptop had twice the memory you had and was running slow so I double the memory (went from 2 to 4gig) and everything really speed up.

Just something to keep in mind if you want to do a small upgrade. Memory has come way down in price.

---

### Post by Ertai87 on 2012-08-23
> **irv said:**
> You posted this a week ago. Is this the first time you tried rebooting? Anytime I have a slow down the first thing I do is try a fresh power down restart, this clears all memory.

Yes I see from your screen shot that you have plugins running in your browser which are taking up most of the memory. This will slow things down.

Also you do not have much memory to begin with. My laptop had twice the memory you had and was running slow so I double the memory (went from 2 to 4gig) and everything really speed up.

Just something to keep in mind if you want to do a small upgrade. Memory has come way down in price.

No, I reboot every day, but I just never had the problem that bad again before yesterday.

The only plugin I should have running is Flash, AFAIK.  Is that data normal for Flash?

My computer is very old; I bought it in March of 2006.  When I bought it, I got the most amount of memory I was offered, and I don't know how to open it well enough to try to start fiddling around with the interior (it's a laptop).  As long as it functions, I'm not particularly interested in changing it, mainly because it's likely going to need to be replaced in the next few years anyway.

---

### Post by irv on 2012-08-23
> **Ertai87 said:**
> No, I reboot every day, but I just never had the problem that bad again before yesterday.

The only plugin I should have running is Flash, AFAIK.  Is that data normal for Flash?

My computer is very old; I bought it in March of 2006.  When I bought it, I got the most amount of memory I was offered, and I don't know how to open it well enough to try to start fiddling around with the interior (it's a laptop).  As long as it functions, I'm not particularly interested in changing it, mainly because it's likely going to need to be replaced in the next few years anyway.
I said the same think about this older laptop I am using. I was looking to get a new one when I installed more memory and a SSD drive. (It is a laptop also). The memory and Hard Drives are the easiest things to changes. If you have any friends who have any experience with computer they should be able to help do this simple thing.

Since I did this to my old laptop I can't tell you how pleased I am with it now, and I don't plan on getting a new one until this one dies. I just checked the boot time on it this morning and it was exactly 20 seconds. And all my apps just run fast.

---

### Post by Ertai87 on 2012-08-23
> **irv said:**
> I said the same think about this older laptop I am using. I was looking to get a new one when I installed more memory and a SSD drive. (It is a laptop also). The memory and Hard Drives are the easiest things to changes. If you have any friends who have any experience with computer they should be able to help do this simple thing.

Since I did this to my old laptop I can't tell you how pleased I am with it now, and I don't plan on getting a new one until this one dies. I just checked the boot time on it this morning and it was exactly 20 seconds. And all my apps just run fast.

I'm actually not even sure this computer is upgradeable; I don't know if it has any unused memory slots at all XD I can look into it though.  Do you think that's the only problem, based on the screenshot I took?

---

### Post by irv on 2012-08-23
> **Ertai87 said:**
> I'm actually not even sure this computer is upgradeable; I don't know if it has any unused memory slots at all XD I can look into it though.  Do you think that's the only problem, based on the screenshot I took?
That's all that jumped out at me.
What kind of laptop do you have? Maybe I can look into it for you to see if it is upgradeable. I have been working on computer since the late 70's.

---

### Post by Ertai87 on 2012-08-23
> **irv said:**
> That's all that jumped out at me.
What kind of laptop do you have? Maybe I can look into it for you to see if it is upgradeable. I have been working on computer since the late 70's.

It's a Dell Inspiron 6400 with 1GB RAM.  I believe it's 2 physical RAM sticks, but not 100% sure on that.

---

### Post by irv on 2012-08-23
> **Ertai87 said:**
> It's a Dell Inspiron 6400 with 1GB RAM.  I believe it's 2 physical RAM sticks, but not 100% sure on that.
After doing some checking the most you can do is 2X1gig giving you  2gig of RAM. It would be somewhat of a improvement but not much. You could use a SSD in place of the Hard Drive which would be another improvement. But over all in your case I don't see doing it. Your laptop is a little older then the one I have so in your case I would consider a new one.

I guess there is a point where should you or should you not upgrade. For the amount of improvement I would have to say no. It was worth looking into though.

I did see that if you went to 4gig 2x2gig and running the 64bit OS you would only see 3.2gig if it would boot at all. You would be taking a change.
Sorry for the bad news.

---

### Post by Ertai87 on 2012-08-23
> **irv said:**
> After doing some checking the most you can do is 2X1gig giving you  2gig of RAM. It would be somewhat of a improvement but not much. You could use a SSD in place of the Hard Drive which would be another improvement. But over all in your case I don't see doing it. Your laptop is a little older then the one I have so in your case I would consider a new one.

I guess there is a point where should you or should you not upgrade. For the amount of improvement I would have to say no. It was worth looking into though.

I did see that if you went to 4gig 2x2gig and running the 64bit OS you would only see 3.2gig if it would boot at all. You would be taking a change.
Sorry for the bad news.

LOL that's about what I guessed would happen.  Thanks for checking into it for me though =D

---

### Post by irv on 2012-08-23
I looked up the price of the memory, it was $18 X 2= $32. And about $128 for a SSD. So do you want to spend $160 for a slight improvement or put the $160 towards a new laptop?

---

### Post by Ertai87 on 2012-08-23
> **irv said:**
> I looked up the price of the memory, it was $18 X 2= $32. And about $128 for a SSD. So do you want to spend $160 for a slight improvement or put the $160 towards a new laptop?

LOL That's about the situation I guessed I was in =P

---

