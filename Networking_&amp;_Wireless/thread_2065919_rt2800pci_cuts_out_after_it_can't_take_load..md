---
title: "rt2800pci cuts out after it can't take load."
date: 2012-10-03
forum: Networking &amp; Wireless
---

### Post by scwogit on 2012-10-03
I am currently using a wireless connection which uses the driver rt2800pci, I have read on the internet how it times out every now and then. I find when I'm downloading a file or have more than one youtube video open it decides just to stop loading the internet, however it shows it is still connected to my wireless it decides to stop. Is there a patch which fixes this problem or a different driver I could install which would work better than my current driver rt2800pci.

I have searched all over google for a solved answer, however I have found threads which claim to be solved in the title but are not solved/ threads that make 100% no sense.

---

### Post by scwogit on 2012-10-03
I will just mention it didn't used to be a problem it has only come about in the last few months it's like it limits how much transfer of data is allowed and clocks out once it hits the bar.

---

### Post by james_xxx on 2012-10-12
I am also experiencing terrible problems with an rt3060-based device, using the rt2800pci driver.

However, in my case it has nothing to do with heavy load. I am experiencing constant packet loss (around 5-20%) when pinging my router.

I just installed the backports modules, which did change rt2800pci version numbers, but that has not helped.

I don't believe I had this problem until relatively recently. I will try to do more testing.

---

### Post by james_xxx on 2012-10-12
I just spent some time in Windows 7, and pinged my router numerous times, doing 50 pings at a time, and experienced no packet loss at all. This influences me even more to believe that there is presently something wrong with the rt2800pci Linux driver.

---

### Post by james_xxx on 2012-10-12
Reporting back again...

I just upgraded to the 3.5.0 kernel (from the xorg-edgers PPA), and although the problem has not completely disappeared, I'm experiencing MARKEDLY reduced packet loss.

Each time I have tested since upgrading the kernel, I get 0 - 10% packet loss, pinging my home WAP.

It's still ridiculous for there to be any packet loss at all, but this is a huge improvement.

---

### Post by andymcca on 2012-11-28
Just wanted to add my $.02...

Noticed some bandwidth issues, so started fiddling around and noticed high packet loss (varies 5-15 % generally). This is happening on a desktop running a RT2790 (rt2800pci driver), and a laptop running a RT5390 (also rt2800pci driver).

The laptop is a dual boot machine with Windows 7. Pinging on Windows repeatably gives 0 packets lost in over 1000 pings. Pinging on Ubuntu with the aforementioned driver predictably yields >5% packet loss.

Dropped packets appear to occur in bursts of 1-5. At a glance, most are single dropped packets, but occur during periods of increased loss.

I'm going to fiddle with gain, etc, and will post back if I have any luck.

 Edit:
I played around with a few things... Compiling newer drivers per
[this askubuntu.com post by mywebslave]("http://askubuntu.com/questions/178547/connection-drops-out-regularly-with-a-ralink-rt2800")
helped quite a bit. I used the latest stable compat-wireless release (3.6.6-1). It may have actually been updated to 3.6.8-1 in the last few hours, so YMMV.

 The laptop now has drop rates approaching (but not quite equal to) the Win7 driver performance. The desktop still drops some packets, but that could be due to the card and location -- I do not have another OS to compare it to.  Turning down the gain via 
sudo iwconfig wlan0 txpower 10 
may have helped slightly, but not a huge amount.

---

### Post by scwogit on 2013-03-02
Hi guys sorry I ended up with commenting a lot on another thread and got my situation almost sorted out. However I didn't return back to the thread to post the answer not realizing anyone would then see it and comment on it. So just for anyone else looking at this thread the following should hopefully help you. 

There are a few things you might want to consider if you are having problems where your rt2800 driver doesn't want to load when you log on then you should use the following terminal code which will hopefully open it up for you....

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r rt2800pci
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe rt2800pci[/FONT][/COLOR]
```

This should reload your wireless and if you currently don't have it working it should start it off.

However this is very nice, it can mean you might have to do it every time you load your computer, my biggest success was to download the windows driver ndiswrapper program. This allows you to select your driver off a download or CD when browsing for it you will want to look for a file ending in .inf mine for axample says rt2860.inf select this. Once this is done put the following into terminal.

```
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo ndiswrapper -ma
sudo ndiswrapper -mi

```

After this we get a little more in depth by going into root and linking up files, 
(I don't recommend you mess around in this too much however the following made my wireless work a charm.)
So type in... 
```
gksudo nautilus
```

This will load root; to do the next part it is best to go file>new tab, which will open another tab, working with the 2 tabs i find to be easier. On the first tab go back to the 'file system' and then click on the 'etc' file. once in this go into your other tab and do the same however then go into the 'modprobe.d' file, look for 'ndiswrapper.conf' right click on it and look for 'link to' click it you will then have a link called 'link to 'ndiswrapper.conf', drag and drop this into the 'etc' tab and rename it 'modules.conf' this will help it to establish a better link especially when loading the computer.


So as I said for me the above worked a charm. since this i have reinstalled ubuntu and done exactly what is written above and I have found it to be successful a second time running.

I hope this helps anyone :)


Should you need more information see...
[http://www.youtube.com/watch?v=wchimaoe9KE&feature=endscreen](http://www.youtube.com/watch?v=wchimaoe9KE&feature=endscreen) and
[http://ubuntuforums.org/showthread.php?t=2042315&page=3](http://ubuntuforums.org/showthread.php?t=2042315&page=3)

---

