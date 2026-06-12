---
title: "Where did my wireless networks go?"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by Baldemar on 2010-04-23
My computer was recognizing wifi networks. All of a sudden none.
I have seen other post and went ahead tried this and got this.

baldemar@baldemar-laptop:~$ sudo iwlist wlano scan
wlano     Interface doesn't support scanning.

---

### Post by Iowan on 2010-04-23
Does **sudo lshw -C network** reveal anything about your interface? (Post results, if possible)

---

### Post by computer13137 on 2010-04-24
If you have a netbook, or some other kind of low power\cheap WiFi card, you may have difficulty detecting your wireless network if you're in a high interference environment.

Just throwing that out there.  Have you recently added any 2.4Ghz equipment to your house? (Phones, etc)

Since it's a laptop\netbook, take it to a hot spot and see if it detects WiFi there.  Do other computers in your house detect your WiFi without a problem?

Cheers,
Kirk

---

### Post by garvinrick4 on 2010-04-24
cat /etc/resolv.conf


Should show your domain and server if nothing there you got nothing going on.

---

### Post by v1ad on 2010-04-24
right click onto the disabled wifi icon and click enable.  i was going crazy till i realized that. it disables at random on reboots.

---

### Post by Baldemar on 2010-04-24
Thanks for the help.. I got it. I did not know there was a turn on/off button on the side of my laptop ,, my son probably turned it of when using it...

---

### Post by Iowan on 2010-04-24
Sometimes it's the simple things...:)
[[SOLVED]]("http://https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

