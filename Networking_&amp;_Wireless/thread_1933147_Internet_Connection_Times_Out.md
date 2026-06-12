---
title: "Internet Connection Times Out"
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by SpiderMan187 on 2012-02-28
Hey guys this is a nice community. Im glad i switched from Windows.

Well got that out of the way! :D

Ok so I have a Netgear WN111v2 Wireless adapter.

I get internet no problems but if I leave the computer on, after a while I the the rotating colorful lines.

Then I can never get it to reconnect. It asks me for the pass and everything but it never comes back on.

I have to restart the PC to get it to work again.


Can anyone help me with this issue?

Thank You very much

---

### Post by gordintoronto on 2012-02-28
Did the WN111v2 work "out of the box"? What version of Ubuntu?

What steps did you take to set up the connection?

---

### Post by SpiderMan187 on 2012-02-29
> **gordintoronto said:**
> Did the WN111v2 work "out of the box"? What version of Ubuntu?

What steps did you take to set up the connection?

At first it did but after the updates installed it stopped connecting.

I did lsusb in terminal and I could see it connected.

So then I followed another post to get it to work.

This is what I did:

For those of you who are having the issue where Ubuntu Network says:

"Network Disabled"

Here is a quick fix for that.

Open terminal.

It is located Applications/Accessories 

Then type in:

sudo service network-manager stop

Then it should have stopped network.

Then type:

sudo rm /var/lib/NetworkManager/NetworkManager.state

Then type in:

sudo service network-manager start

Then the type:

sudo reboot

Thats it!

#####################

That's how I got it work after that.

No after an hour or so it gives me those blue arrows and I can't reconnect unless I reboot

---

### Post by SpiderMan187 on 2012-03-01
Any ideas on what to do to solve this issue?

Thanks

---

### Post by SpiderMan187 on 2012-03-14
Well I moved my modem next to my pc and now I am connected directyl to it without any issues.

Thanks

No More wireless

---

