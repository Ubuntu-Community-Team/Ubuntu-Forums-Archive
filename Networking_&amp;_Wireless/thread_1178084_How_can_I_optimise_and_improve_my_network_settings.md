---
title: "How can I optimise and improve my network settings and increase my Ubuntu Downlods??"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by -=Ghost=- on 2009-06-04
Hi Guys...

I have been running Ubuntu 9.04 for some time now.

 I have been suffering from very slow Download speeds on a regular basis.

My Download speeds have never really been above 160 kb/s.
And more often than not they are as low as 40kb/s.
This is at any time of the day or night, and irrelevant of what I am Downloading.

Also it makes little difference whether I connect Wirelessly or by Ethernet!

Even using various Download managers only improves my speeds sightly.

I should be able to enjoy speeds of around 800 kb/s

How can I optimise and Improve my network configurations?

Also What can I do to increase my Browsing speeds and also my downloads? 

I look forward to any replies.

---

### Post by infinitejones on 2009-06-04
> **-=Ghost=- said:**
> 
I should be able to enjoy speeds of around 800 kb/s


One thing that springs to mind - where do you get this number from? Is it something that your ISP is telling you, or have you definitely had download speeds this fast before?

Don't forget, ISPs tend to quote "maximum theoretical" broadband speeds under perfect conditions, but lots of factors that none of us can control (eg. distance from the telephone exchange and quality of wiring between you and the exchange) can affect it.

Also, do the speeds appear to have dropped since you started using Ubuntu, or have they always been lower than you expect (eg. the same if you've used Windows)?

There are a couple of things you can try:

1) Try using [www.speedtest.net](www.speedtest.net) a few times, at different times of day, to get an overall average
2) Then, if possible, do the speedtest.net tests again using a different OS - borrow a Windows laptop or something.

That way, if the speeds only drop when you use Ubuntu, you'll know whether that the problem is caused by settings in Ubuntu (which you can try to adjust).

If the speed is consisently lower than expected, it's something less easy to control, as mention in my second paragraph above.

I have to say, I don't need to change the default network settings in Jaunty (TTL, MTU etc) to get the maximum possible download speed from my ISP, for the area I live in. I say this because I also run Windows and OSX on other machines at home, all with their default network settings, and I always get the same average results on speedtest from all machines and all OSes. So it's safe to assume that the default network settings in Ubuntu don't affect download speeds any more or less than the default settings in eg. Windows.

---

### Post by -=Ghost=- on 2009-06-04
Hi infinitejones.

I have definitely had the 800 kb/s plus download speeds in the past and  More so when I was using 8.10.

This is why I am a little miffed on why my speeds are showing such a decrease.

I have a dual boot sytem with Vista Premium and Ubuntu 9.04, Eacch on there own seperate Partition. So I'm pretty sure it is not my windows firewall causing any issues!

My Download speeds in Vista are on the most reaching around the 800kb/s. Mainly because I use sytem mechanic 8, its great for optimising Vista's settings automatically.

This is another reason why I think there is something that can be rectified within Ubuntu to improve my download speeds, because as I say, my windows Downloads are markably better...

---

### Post by infinitejones on 2009-06-04
So maybe it's worth doing a bit of trial-and-error changing of the MTU.

The easy way looks like doing this:

System -> Preferences -> Network connections, then click on the active one, then click edit. You should see where you can change the MTU, so then I guess it's going to be a case of trying various settings and see which ones provide you the best download speeds. Maybe find out what MTU Windows is using and change Ubuntu's to that?

As for the harder way, a bit of googling also provided [this link]("http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html") which gives some suggested values based on the nature of your network (I would imagine either 1500 or 1492, unless you know it's something different), plus tells you how to change it via the command line. Don't forget, if you go down the route of editing /etc/network/interfaces, create a backup of it first: ```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

Googling for things like "[Linux adjust MTU]("http://www.google.com.au/search?q=Linux+adjust+MTU&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a")" or "[linux adjust TTL]("http://www.google.com.au/search?q=linux+adjust+ttl&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a")" brings lots more links you could have a look through.

As for automatically adjusting it, like with Norton, I couldn't find anything. That's kind of the point of Linux though - most settings can be altered manually just by editing a text file (like /etc/networks/interfaces), and while you need to think about what you're doing and remember to ALWAYS BACK UP THE FILE YOU'RE CHANGING FIRST, in case something breaks, it means you just need to spend a little time tweaking to find what works best for you. 

Plus, hopefully, you'll learn something you didn't know before, and for me, that's one of the best things about using Linux!

---

