---
title: "Clearing pppoeconf settings"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by ittiam on 2009-01-27
I want to clear the configuration done using pppoeconf. I think pppoeconf is causing problems whenever I want to connect to a wireless network using wpa_supplicant. Can someone tell me how to clear the pppoeconf settings?

Thanks

---

### Post by ranch hand on 2009-01-28
```

sudo pppconfig

```
Your menu will come up and you will see the option
> 
 Delete Delete a connection 

click it.

You will then get a list of connections.  Click what you want removed and then leave pppconfig the same way you did when you set it up.

I had to do that to get dial up to work in 8.10.  It was easier than it was in 8.04 to set up.  I was making it too hard.

Hope this helps.

---

### Post by ittiam on 2009-01-28
I actually kind of deleted the dsl-provider entry in the /etc/network/interfaces file before doing pppconfig. So when i run pppconfig and select delete a connection, it shows no connections? Am I right, I know I kind of messed up by changing the /etc/network/interfaces file first but could you please let me know the manual way of clearing stuff, like can i just remove the files in the folder /etc/ppp/peers? I can sense it is doing something during startup because of which my wireless does not work but I am not able to find what

---

### Post by ranch hand on 2009-01-28
When you get into these files it is better to comment stuff out than to remove them.  This way if you need them you can easily restore them.

I assume that you removed the file that was the name of the connection in pppconfig that was installed in /etc/ppp/peer.  It would have been better to rename it "filename"backup and leave it there.  It just leaves you the option of restoring things.

Yes that would clear pppconfig.

I use dial up and will soon have the chance to have DSL.  Where I am now is not even close to cell towers let alone wireless internet connections.  I am not sure what those entries in /etc/network/interfaces would be.

I would try renaming files/folders or renaming them and start over on yur configuration of wireless.  Then when you get it right you can see what was really the problem and what was not.  You can also remove the unneeded stuff at that point.

I am not sure that your problem is really where you think it is.  I ran a quick search and there are some interesting things that you may want to read before going further.

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276508](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276508)

[http://ubuntuforums.org/showthread.php?p=6360321](http://ubuntuforums.org/showthread.php?p=6360321)

[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/272185](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/272185)

These may give you a hint at where else to look for you problem.

---

### Post by ittiam on 2009-01-28
I have successfully configured wireless with ndiswrapper and wpa_supplicant number of times. But then I did some mess in some file because I wanted to remove dsl connection configuration and from then on wpa_supplicant is not working. Wireless comes on when I try it using knetworkmanager. 

Here is another post of mine that might give you more details:

[http://ubuntuforums.org/showthread.php?t=1052494](http://ubuntuforums.org/showthread.php?t=1052494)

---

### Post by ranch hand on 2009-01-28
I would comment out the following;
```

auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf -B
post-down killall -q wpa_supplicant

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```
from your /etc/network/interfaces file for a start.

I have little experience with DSL and non with wireless.  That said, I a suprised that you need to configure DSL in pppconfig.  I thought I needed to and found that in Ubuntu Hardy it took 2 clicks in NM and in Intrepid it took nothing at all, just boot up and you are connected to the system here in SE Montana.

---

### Post by ranch hand on 2009-01-28
DON'T.

I am nuts.  It is just the last 2 lines need commenting out.

---

### Post by ittiam on 2009-01-28
I used pppoeconf. I mean I had to do it, it did not work out of box. I did try deleting the eth0 from the network interfaces file! No avail.

---

### Post by ranch hand on 2009-01-28
I wouldn't delete it.  eth0 is there and should be documented.  I would comment it out.
```

 gksudo gedit /etc/network/interfaces

```
should get you in there.
```

## auto eth0
## iface eth0 inet dhcp

```
is what you want it to look like.  The process will ignore it now.

Save and close and try it.  See what happens.

---

### Post by ittiam on 2009-01-28
Ok I made some progress

i found this process runnning

```

/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log

```
I killed this and voila wpa_supplicant works.

Any idea what is going on



EDIT: posted the wrong process

---

### Post by ranch hand on 2009-01-28
You are talking about wirerless to a guy that chases cows for a living.  The cows outnuber the local population by about 100 - 150 times.  There really is a lack of wirerless tecnology here.  I haven't a clue.

I know how I felt when I got the dial up modem to work though and I suggest you celebrate.

That might be implicated in one of the bug reports, I don't know.  I know a lot of people have 2 or 3 ways to connect.  There may be some conflicts with wireless.

I just spent hte last hours updating to kernal 2.6.24-11.  This is slow on dial up.  We are so far from town that the speed is about 4.4Kb/s on good days.  Today is not one of them.  Tunning about 3.3.  I think I could get used to more speed without it spoiling me.

Glad you are up.  Have fun.

---

### Post by ranch hand on 2009-01-28
Ignore, some grumpy old guy did a double post.  Geez some people.

---

### Post by bhadotia on 2011-01-03
> **ranch hand said:**
> ```

sudo pppconfig

```
Your menu will come up and you will see the option

click it.

You will then get a list of connections.  Click what you want removed and then leave pppconfig the same way you did when you set it up.

I had to do that to get dial up to work in 8.10.  It was easier than it was in 8.04 to set up.  I was making it too hard.

Hope this helps.

Hi I also want to undo the changes made by pppoeconf because i got a new router which no longer works in bridge mode as my earlier router. 
[QUOTE=ittiam]I actually kind of deleted the dsl-provider entry in the /etc/network/interfaces file before doing pppconfig. So when i run pppconfig and select delete a connection, it shows no connections? Am I right, I know I kind of messed up by changing the /etc/network/interfaces file first but could you please let me know the manual way of clearing stuff, like can i just remove the files in the folder /etc/ppp/peers? I can sense it is doing something during startup because of which my wireless does not work but I am not able to find what[/QUOTE]
I haven't changed anything after I ran pppoeconf for configuring my network connection but still I don't see the name of my dsl connection when i run the above command.
I googled to find a solution and know about the files which are modified by pppoeconf. But I was hoping to find a automatic solution like the above because that would be cleaner.
So, any ideas on this?

---

### Post by bhadotia on 2011-01-04
> **bhadotia said:**
> 
so, any ideas on this?

bump!

---

### Post by dineshs on 2011-01-04
I think pppoeconf will 
1)edit /etc/network/interfaces
example> auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual and 
2)create a file dsl-provider(default)in /etc/ppp/peers.please check using```
gksudo nautilus /etc/ppp/peers
```
Note:If you are using network manager, /etc/network/interfaces will have only the first 2 lines

---

### Post by bhadotia on 2011-01-04
> **dineshs said:**
> I think pppoeconf will 
1)edit /etc/network/interfaces
example and 
2)create a file dsl-provider(default)in /etc/ppp/peers.please check using```
gksudo nautilus /etc/ppp/peers
```
Note:If you are using network manager, /etc/network/interfaces will have only the first 2 lines

Yes I know about that but still thank you. But what i was actually asking for is an automatic method to undo the changes made by pppoeconf so that nothing is left behind

---

