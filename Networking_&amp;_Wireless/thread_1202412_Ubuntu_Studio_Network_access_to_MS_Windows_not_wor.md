---
title: "Ubuntu Studio: Network access to MS Windows not working"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by Gerd Oestringer on 2009-07-02
I have installed Ubuntu Studio from CD and updated it online. I got as far as mounting an external disc and accessing the internet. What I don't get working is the access from Ubunto to my windows xp machine (it works the other way round though).
Yesterday I accidently deletedt the IP address of my DSN server (router) from out of the NETWORK configuration. After that I could access the windows machine, but the Internet connection was gone. Putting in the IP address again, the situation reversed again.
Any ideas ? Your help is greatly appreciated .... I am a complete newby on LINUX

Thanks, Gerd

---

### Post by superprash2003 on 2009-07-02
presuming you mean DNS ips , try opendns servers 208.67.222.222 and 208.67.220.220 , and when trying to access windows machines , try accessing via ip instead of hostname

---

### Post by Gerd Oestringer on 2009-07-03
Thanks, Superprash

1. Yes, I meant DNS
2. I changed the DNS IP in NETWORK to the ones provided by you, my Internet access still works :p
3. I created another 'Connect To Server' entry (windows share) using the IP address of my windows computer. I still get the error "**Failed to retrieve share list from server**".
4. Pinging the IP address of my windows computer  from a terminal process works fine.

Thanks for any further help.

---

### Post by superprash2003 on 2009-07-03
that error is common , its a bug ,try this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html) . if you see this error again , try refreshing multiple times

---

### Post by Gerd Oestringer on 2009-07-04
I tried it and it immediately worked. I just hope the configuration is saved and I don't need to do this each time.

Next I'll go thru your tutorials, sure I will learn a lot there.

Many thanks.

---

