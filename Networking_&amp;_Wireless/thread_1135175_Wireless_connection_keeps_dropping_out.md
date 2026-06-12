---
title: "Wireless connection keeps dropping out"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by eyescovered on 2009-04-24
hey all. new ubuntu user here. i'm making an attempt to make the full switch, but i'm having a problem. i use a hidden ssid and mac filtering. i can connect to my wireless but after a few minutes it'll appear to be still connected, but no sites will load. i can delete the connection and try again and the same thing will happen. i'm using the new 9.04 version with an hp compaq 6510b. any ideas?

sorry if this already posted, if so, just provide a link to that thread.

---

### Post by rlzyoner on 2009-04-24
There's a few things you can try.
Assuming the network manager indicates that you have connected to the network.

Try pinging out.
```
ping -c 4 www.google.ie
```

Another thing could be to tracepath
```
tracepath www.google.ie
```

Also, ensure that you are getting an ip address from the router

```
ifconfig
```
And ensure that the details for the correct adaptor look something like
inet addr:192.168.1.199

One other thing to try might be open up your network connections and manually enter the dns addresses.
I've sometimes had to do this for wired connections.

---

### Post by eyescovered on 2009-04-24
k thanks. i'm at work right now, so i will try that as soon as i get home. i live in the usa, so i'm assuming i'd use .com instead of .ie

---

### Post by rlzyoner on 2009-04-24
In work myself so I know what your going through :)
Roll on 5.30

But anyway, yeah replace [www.google.ie](www.google.ie) with [www.google.com](www.google.com)

All the ping does is send packets and ensure that it gets replies.

The tracepath just prints out how packets reach their destination.

Thus you'll be able to see if the packets are getting as far as your router and just stopping there.

Let us know if you get it sorted

Peace

---

### Post by eyescovered on 2009-04-24
much thanks!!! i really do want to make ubuntu my primary os! and (obviously) this is a big hang-up. other than that, i have a zune so i'll have to play around with virtualbox to see if it works ok. otherwise, i may need to dualboot. i've seen a few posts about it on here already. also, i'm looking for a good mp3 ripper.

---

### Post by rlzyoner on 2009-04-24
Yeah the wireless was the only reason I was dualbooting for the first few months.
Then as soon as I got the wireless going, i dropped windows.

Not too sure on the mp3 ripper ?
Maybe one for the other threads.

---

### Post by eyescovered on 2009-04-28
ok, my connection is fine, but i have to manually connect everytime i start my computer. how do i get it to automatically to it? i have the 'Connect automatically' box checked but it doesn't seem to be working. any ideas?

---

### Post by eyescovered on 2009-04-29
bump

help, please?

---

