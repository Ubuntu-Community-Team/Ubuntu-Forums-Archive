---
title: "Zoneminder web interface not loading"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by andrew nz on 2010-07-31
Hi Guys

i've followed this [guide to installing zoneminder]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBIQFjAA&url=http%3A%2F%2Fwww.howtoforge.com%2Fvideo_surveillance_zoneminder_ubuntu&ei=2MlTTIKxFJPSsAOZ1KHaAg&usg=AFQjCNEMry9wvVjCfDidz73hHGsQjJILiw&sig2=J1qIfI8C3O2vXiL12-BPCA") i'm running apache2 web server already and can be accessed from internet as well as locally.

i think this is causing problems to:

  ```
sudo ln -s /etc/zm/apache.conf /etc/apache2/conf.d/zoneminder.conf 
```because when i run apache2 it does this:
```
sudo /etc/init.d/apache2 force-reload 
 * Reloading web server config apache2                                          [Sat Jul 31 19:03:27 2010] [warn] The Alias directive in /etc/apache2/sites-enabled/apache.conf at line 1 will probably never match because it overlaps an earlier Alias.
```so i've jsut modified the file to read:

##Alias /zm /usr/share/zoneminder

##<Directory /usr/share/zoneminder>
##  php_flag register_globals off
##  Options Indexes FollowSymLinks
##  <IfModule mod_dir.c>
##    DirectoryIndex index.php
##  </IfModule>
##</Directory>

putting the ## in their and resaving file, resolves that problem, but i think it may have something to do with why zm interface is not workling/accessable.


i'm sure it'll just be one line of text in a config file that is stopping it from running. it taken a lot of fiddling round to get ushare apache2 and my network running together.

any suggestions?




and heres my ifconfig eth0
```
andrew@ubuntu2:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0a:e6:95:27:f4  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e6ff:fe95:27f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4519 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5011 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3461172 (3.4 MB)  TX bytes:890115 (890.1 KB)
          Interrupt:22 Base address:0xcc00 
```

---

