---
title: "SSH worked yesterday, but fails this morning."
date: 2012-09-12
forum: Networking &amp; Wireless
---

### Post by Alevins5 on 2012-09-12
Yesterday I moved into my new house. I got my machine running Ubuntu 12.04 to act as a server and handle wireless printing/minecraft server/remote ssh all from anywhere using a domain name provided by dyndns; with WOL working locally as well, so I was pretty excited. This morning, however, I went to boot it up using WOL, and it worked. I was able to connect via my phone over a command line ssh shortcut app, but then it all stopped working. I couldn't connect via any of the things that had been working last night. Wireless printing still works, though. So I don't quite understand what's going on.

What's weirder still is that my app on my phone shows the server is online through DNS, but when I try to connect there is an error. But the app can't see the server running locally, and shows it as offline. I had no luck sshing in through my mac locally or through the DNS, either. The connection always seems to time out.

I am running 12.04 on my ubuntu machine and tomato on my router. I get the feeling that this has something to do with the router, but I don't know what settings to check. Any help would be much appreciated!

---

### Post by Lars Noodén on 2012-09-12
Can you connect via SSH to the machine locally using 127.0.0.1 ?

If so, can you connect via the LAN using the LAN's private address? 

What does the ip number returned by your dyndns hostname match the actual ip number in use by your router?  Look both up manually and compare.

---

### Post by Alevins5 on 2012-09-12
So as it turns out, as I was mucking around in the Bios, I turned off USB support for the OS. For some reason, it appears as if that was preventing me from accessing the computer through the network, because that was the only thing I changed and then suddenly the computer started working. Thanks anyways for your help! Not sure why it works now, but it does! :)

---

