---
title: "Cannot connect to local web server"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by rplantz on 2009-03-14
I have set up a web server that I'm keeping private on my LAN for learning and experimentation. (See [http://ubuntuforums.org/showthread.php?t=1094258](http://ubuntuforums.org/showthread.php?t=1094258))

Running Firefox 3.07 on Vista I can simply enter
```

bob-desktop/~bob

```
as the URL and it connects to my local web server.

But in Ubuntu and Mac OS X, the same request causes Firefox (and Safari on the Mac) to do a Google search. If I enter
```

http://bob-desktop/~bob

```
both Ubuntu and Mac OS X fill in
```

http://www.bob-desktop.com/~bob

```
for (to?) me.

Can anyone explain this to me? Or point me to some good sources for an explanation? I suspect that Ubuntu and OS X are doing the "right" thing, but I would like to understand it.

The irony here is that I'm used to Microsoft software doing things for/to me that I really don't want to happen. In this case it seems to be Linux/OS X that are "helping" me.

-- Bob

---

### Post by puppywhacker on 2009-03-14
"bob-desktop" is the hostname which is mapped to an ip-address. I guess on your windows machine that is 127.0.0.1 which is the localhost. So it makes sense that windows can resolve itself. On OSX and linux the resolving is done using the file named /etc/hosts and if the hostname isn't listed it will use the DNS server found in /etc/resolv.conf

Since firefox and safari (not linux or macos) can't resolve "bob-desktop" they start guessing you must have meant [www.bob-desktop.com](www.bob-desktop.com) which is here a wrong guess. you could connect to the server by using an ip address in the URL like this  [http://192.168.1.2/~bob](http://192.168.1.2/~bob)

If you want the url like you posted to work, add a line in the /etc/hosts 
```
192.168.1.2 bob-desktop
```

This story is not operating system specific so the above also applies to windows.

---

### Post by rplantz on 2009-03-14
> **puppywhacker said:**
> "bob-desktop" is the hostname which is mapped to an ip-address. I guess on your windows machine that is 127.0.0.1 which is the localhost.


No, Vista is "bob-pc". "bob-desktop" is my Ubuntu desktop machine, which is where my web server is. (I didn't make this clear in this post; it's explained in the one I referenced.)

> 
You could connect to the server by using an ip address in the URL like this  [http://192.168.1.2/~bob](http://192.168.1.2/~bob)

Yes, this works. But since I've set my router to use DHCP, I need to look up my web server's IP address each time I reboot.

> 
If you want the url like you posted to work, add a line in the /etc/hosts 
```
192.168.1.2 bob-desktop
```
[/code]

My router is set up for DHCP. I would have to change that to static (local) IP addresses if I want to use /etc/hosts. Since Vista can resolve the name (presumably) from my router, I'm trying to figure out why Ubuntu and OS X cannot.

I can make all this work. But it seems to be OS-specific, and I'm trying to learn more about how all this works. There must be a way to tell Ubuntu (and OS X) to try to resolve the URL at my router level, where it is a simple host name.

---

### Post by puppywhacker on 2009-03-14
vista uses UPnP to do network discovery. I think it uses IGMP to join a multicast where services are advertised. more and more routers support this.

If you really want to learn, you can make a network trace with wireshark (on windows and linux and probably OSX aswell) it will show you exactly which protocols are on the wire.

---

