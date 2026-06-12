---
title: "Proxy &amp; Synaptic Package manager"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by fatmal on 2009-01-16
Howdy,

At work I need to use a proxy to access the internet, so I need to set the proxy server (System - Preferences - Network Proxy - Manual Proxy Config). I also manually set that proxy server in the Synaptic Package manager (Setting - Network).

Am at home now (on ADSL), and can search repositories but not download the packages. I have reset the network proxy *and* the proxy setting in Synaptic to Direct Internet Connection, however, any download (using Synaptic or apt-get from command line) fails because it can't resolve the proxy.

It seems to me that there is another proxy setting hiding somewhere - any help finding it would be much appreciated.

Thanks in advance!

Mal.

---

### Post by veloce on 2009-01-22
> **fatmal said:**
> Howdy,

At work I need to use a proxy to access the internet, so I need to set the proxy server (System - Preferences - Network Proxy - Manual Proxy Config). I also manually set that proxy server in the Synaptic Package manager (Setting - Network).

Am at home now (on ADSL), and can search repositories but not download the packages. I have reset the network proxy *and* the proxy setting in Synaptic to Direct Internet Connection, however, any download (using Synaptic or apt-get from command line) fails because it can't resolve the proxy.

It seems to me that there is another proxy setting hiding somewhere - any help finding it would be much appreciated.

Thanks in advance!

Mal.

This is a bug in Synaptic.  For some reason you cannot "unset" the use of a proxy.  Changing it to "direct connection" is just ignored.  The only thing you can do is change the proxy to something else.  I turned on the proxy on my firewall at home so I can point it at that.

The bug has been reported but I haven't seen any action on it.

UPDATE: The bug appears to be fixed.  Not sure when it happened but it all works now.

---

### Post by mistrynitesh on 2009-01-25
This might sound intriguing....
I am using 8.10 on live-usb (persistent mode). I boot it on a computer sitting behind a proxy. So I set the proxy and Firefox is good to go. But Synaptic doesn't work. I check the network settings and it is all correct. Then just to try, I click on Direct Internet Connection in Synaptic --> Settings --> Preferences --> Network. And guess what, it started working. :o Try if something like this works on your computer. ;)

---

### Post by Earl_Maroon on 2009-03-01
I was having this issue myself. It was fixed by setting a proxy and unsetting it in Synaptic.

---

### Post by davidovp on 2009-03-02
_SOLVED:_

If you set the proxy for Synaptic Package Manager through the GUI, it sets the proxy in /etc/apt/apt.conf

After removing the proxy entry in this file manually, SPM worked without using a proxy server.

Hope this helps.

---

### Post by SteoanK on 2009-03-12
I was having a similar issue at work with Ubuntu 8.10. It turns out when I set the proxy to work globally, it doesn't set the proxy settings for synaptic. Once I added in the proxy server info and port it all worked (albeit slow).

---

### Post by SteoanK on 2009-03-12
> **SteoanK said:**
> I was having a similar issue at work with Ubuntu 8.10. It turns out when I set the proxy to work globally, it doesn't set the proxy settings for synaptic. Once I added in the proxy server info and port it all worked (albeit slow).

And now I'm having the issue that everyone else seems to be talking about. Once I get home from work I can't take the proxy settings out of SPM. It just still thinks it is even when I change them. Anyone fix this yet? I tried turning certain proxies on and this one off, and I have a black apt.conf file.

---

### Post by veloce on 2009-03-12
> **SteoanK said:**
> And now I'm having the issue that everyone else seems to be talking about. Once I get home from work I can't take the proxy settings out of SPM. It just still thinks it is even when I change them. Anyone fix this yet? I tried turning certain proxies on and this one off, and I have a black apt.conf file.

Funny, mine seems to be working now - in that I can turn off the proxy. I assumed it was fixed in a recent update.

---

### Post by SteoanK on 2009-03-13
> **veloce said:**
> Funny, mine seems to be working now - in that I can turn off the proxy. I assumed it was fixed in a recent update.

I don't think it was fixed. It took some tinkering with turning on and off certain proxy settings but mine turned off for SPM. I think the trick is to turn synaptic's off before you turn off the network proxy system wide.

I guess I'll find out today when I get home from work (using the proxy!)

---

### Post by veloce on 2009-03-15
> **SteoanK said:**
> I don't think it was fixed. 

Oh great, another timebomb waiting to catch me out when it can be the biggest problem!

---

### Post by waffen on 2009-03-25
Hello,

any progress with this? I have the same issue... :(

---

### Post by andy_ryan on 2009-04-21
the work around of changing the proxy settings is SPM first and then the system settings works.

if you've tried doing it the other way around, that is you have both proxys disabled, but you still get an error (personally i was getting 403 for evrything):
1. turn on the proxy in system settings, DO NOT PRESS APPLY SYSTEM WIDE
2. go to SPM, check use proxy settings,
3. click apply
4. click use direct connection
5. click apply
6. disable proxy in system settings (im not sure if pressing apply system wide is nessesary at this point

wait this worked once and now i get the same problem again sorry

---

### Post by shrik_kshir on 2009-04-22
hi, this is my first post

i'm behind a university proxy which requires authentication; so i tried the foll. ways (on intrepid):

1. set the appropriate fields in synaptics packet manager (GUI) synaptic packet manager ->preferences->network
2. edit apt.conf file as : Acquire::http: proxy "http://user: psswd@proxy: port/";
3. append to bash.bashrc file: export http_proxy = [http://user: psswd@proxy: port/]("http://user:psswd@proxy:port/")
4. setting appropriate fields in system->preferences->network proxy and applying system-wide

(i did these steps in the order 4-1-3-2)

however nothing seems to work; i keep getting the error :"407 proxy authentication required" whenever i try to do sudo apt-get update

please help 
(could the problem be because i have a "$" character in my psswd or "_" character in my username?)

---

### Post by Happy Days on 2009-04-29
Same problem here.  I set my system wide settings while I was at work and now, when I get home, apt-get doesn't want to change back to direct connection.  It is still trying to go through the work proxy.  I tried to edit the apt.conf file - but to be honest I don't know quite what to do.

This is killing me softly...please help.


Well this morning I started up again and it all seems to be doing exactly what it should.  I checked that both SPM and global network proxy was checked for direct access and low and behold it was working.  Could a restart have solved the problem after I changed settings?  Can anyone confirm this?

---

### Post by Happy Days on 2009-05-01
should have made that a new post - bump reasons

---

### Post by veloce on 2009-05-03
> **Happy Days said:**
> 
Well this morning I started up again and it all seems to be doing exactly what it should.  I checked that both SPM and global network proxy was checked for direct access and low and behold it was working.  Could a restart have solved the problem after I changed settings?  Can anyone confirm this?

I've never had a reboot fix this issue.

Luckily, I have a proxy server at home.  It's normally running in invisible mode but I can change the proxy setting to point to it.

I had hoped that Jaunty would have fixed this but unfortunately not.

---

### Post by robert.d on 2009-05-15
I wanted to say that I have the same problem and successfully overcame it using andy_ryan's workaround. I'm repeating it here using the specific steps that worked for me.

1. Turn on the proxy in system settings: "System->Preferences->Network Proxy".
    DO NOT PRESS APPLY SYSTEM WIDE
2. Click [Close]
3. Go to Synaptic Package Manager and check "Manual proxy configuration": "Settings->Preferences->Network". (I also filled in the details with my work proxy server settings.)
4. Click [Ok]
5. Go back into Synaptic Package Manager and check "Direct connection to the internet"
6. Click [Ok]
7. Go back into System->Preferences->Network Proxy".
8. Disable proxy in system settings. (I did not apply system wide.)
9. Click [Close].

After going through these steps, I was then able to successfully install packages.

---

### Post by zabzoo on 2009-09-07
If you use Authentication, ensure that your password doesn't contain a @ symbol - it also doesnt work, because when connecting through the proxy, after the username : password is an @ in the "connection string" if you want to call it that, and when the password contains an @ - it screws it up!

---

### Post by Kokroach on 2009-09-16
Hi - my first post on this great forum. On top of your problem I can add freezing of my Synaptic GUI when I change between Proxy and Direct in Network tab and hit either Apply or OK buttons. I use 9.04 and problem just started yesterday, proving that I should always track the updates I install - apparently something I installed recently clashes with Synaptic. But I don't complain, this system is for free - Long Live Ubuntu!!!

---

### Post by sakthidaran on 2009-10-16
> **fatmal said:**
> Howdy,

At work I need to use a proxy to access the internet, so I need to set the proxy server (System - Preferences - Network Proxy - Manual Proxy Config). I also manually set that proxy server in the Synaptic Package manager (Setting - Network).

Am at home now (on ADSL), and can search repositories but not download the packages. I have reset the network proxy *and* the proxy setting in Synaptic to Direct Internet Connection, however, any download (using Synaptic or apt-get from command line) fails because it can't resolve the proxy.

It seems to me that there is another proxy setting hiding somewhere - any help finding it would be much appreciated.

Thanks in advance!

Mal.
I also had this problem and some how solved it with out knowing what exactly was done. Today, I had the same problem while at home. This is a new computer. I installed Ubuntu9.04 at office. I had set proxy settings. Worked well and downloaded the updates. When I came back home, I had similar problem with wireless network. I changed the system proxy setting to direct connection and synoptic preferences to direct connection. Even restart did not help. **[COLOR="Blue"]Finally, I found a “shutdown” and “poweron” set the system alright.[/COLOR]**

Sakthidaran
Ubuntu 9.04 32bit on Lenovo G450, Core2 Duo T6600 @ 2.2 Ghz, .3 mp webcamera

---

### Post by antid0te on 2009-11-06
> **robert.d said:**
> I wanted to say that I have the same problem and successfully overcame it using andy_ryan's workaround. I'm repeating it here using the specific steps that worked for me.

1. Turn on the proxy in system settings: "System->Preferences->Network Proxy".
    DO NOT PRESS APPLY SYSTEM WIDE
2. Click [Close]
3. Go to Synaptic Package Manager and check "Manual proxy configuration": "Settings->Preferences->Network". (I also filled in the details with my work proxy server settings.)
4. Click [Ok]
5. Go back into Synaptic Package Manager and check "Direct connection to the internet"
6. Click [Ok]
7. Go back into System->Preferences->Network Proxy".
8. Disable proxy in system settings. (I did not apply system wide.)
9. Click [Close].

After going through these steps, I was then able to successfully install packages.
It works..thx a lot ;)

---

### Post by Minister on 2010-10-08
Hi All,

I know this post is old and not many will read to the end, but for whatever it's worth, 

it appears you need to **REBOOT** after clearing the proxy settings in Synaptics Package Manager and then in System Preferences->Network Proxy.

I thought that goes against the whole Linux philosophy - Reboot after clearing the proxy setting ?!?!?!

---

### Post by mjsh401 on 2010-10-10
Hello Every one
I installed ubuntu 10.04 on a computer in my university. I want to  connect to internet. when I do that in win xp I use proxy  192.168.4.10:8080. also for connecting I enter an authentication  username and password. But when I enter these setting in Synaptic  Package Manager from Setting>Preference>Network it cannot connect  to internet. It is intresting for me beacause I can connect to internet  by firefox.
plz help me freinds.

---

### Post by yasir.elsharif on 2011-02-17
I am having the same problem here and I tried all the suggestions and none solved my problem.
I can not  change the proxy settings back to without proxy in synaptic and the whole program freezes when I press ok or apply.
when I ran synaptic from cli I got this error:
```

me@ubuntu~$ sudo synaptic 

(synaptic:18681): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(synaptic:18681): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(synaptic:18681): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(synaptic:18681): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

```

help help please :(

---

