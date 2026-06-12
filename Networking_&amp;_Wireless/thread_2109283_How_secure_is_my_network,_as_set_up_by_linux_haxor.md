---
title: "How secure is my network, as set up by linux haxor"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by artificialname on 2013-01-27
Hi
I followed these instructions to succesfully set up a wireless home network, from my linux desktop to my mac book pro laptop

[http://www.linuxhaxor.net/nixies-linux-haxor-quickie-setting-up-file-sharing-between-windows-linux-and-macs-with-samba/](http://www.linuxhaxor.net/nixies-linux-haxor-quickie-setting-up-file-sharing-between-windows-linux-and-macs-with-samba/)

How secure is it? I don't need any fancy security - just something basic so I don't get hacked! (I hope I have not made any newbie mistakes in the way my network is set up eg advertising an open network that others can access easily)

Next, I'd like to share more then just the "myshare" folder, so any advice on how to make my network more secure will be very much appreciated!

ALSO: My aim is to share an internal hard drive on my desktop with my macbook pro - am i going about this the right way? Should I be using Samba?

---

### Post by prodigy_ on 2013-01-27
Well, **chmod 0777** is almost always a bad idea (not just for shared folders) because it means full access for everyone. It's the easiest solution in many cases but it's not secure. You probably want to read something about Linux file permissions to understand what you're doing: [http://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](http://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions)

On the other hand **security = share** is probably too complicated with unclear benefits. I'd go with **security = user** instead. There's a good HOWTO in the Community section: [https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

You also mentioned WiFi. To secure WiFi you generally want to enable WPA2 security and use a strong password.

---

### Post by artificialname on 2013-01-27
thanks prodigy_

what about AFP with these settings?
[http://missingreadme.wordpress.com/2010/05/08/how-to-set-up-afp-filesharing-on-ubuntu/](http://missingreadme.wordpress.com/2010/05/08/how-to-set-up-afp-filesharing-on-ubuntu/)

Do I need to worry about security with those settings?

---

