---
title: "Can't connect to AFP share from my Mac"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by bobbob1016 on 2011-01-27
I followed these directions: [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

But whenever I try to connect from my Mac to my Ubuntu AFP share, I get "invalid username/password".  I have the correct username/password entered, so I think there is a configuration step that I can't find.  I'd appreciate any help.

---

### Post by bobbob1016 on 2011-01-30
Bump

---

### Post by iTimOSX on 2011-01-31
I Have the same problem I Think we are both on Snow Leopard.
Same error 
Do we need to create an account using the terminal or something?

Tim,

---

### Post by diff_sky on 2011-03-05
Hi,

I followed the tutorial at [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/) and got the same connection error.

It's possibly an issue with the afpd conf:
/etc/netatalk/afpd.conf

I was using version 2 of the netatalk package and needed to specify 'uams_dhx2.so' instead of 'uams_dhx.so'. 

Like so:
- -transall -uamlist uams_randnum.so,uams_dhx2.so,uams_guest.so -nosavepassword -advertise_ssh

Note 'uams_guest.so' is for if you want guest access. See this for more info: [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#comment-48423](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#comment-48423)

Making that change and then restarting the netatalk daemon:
    sudo /etc/init.d/netatalk restart
got everything working. Hope that helps.

---

### Post by Melpomene on 2011-04-15
> **diff_sky said:**
> Hi,

I followed the tutorial at [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/) and got the same connection error.

It's possibly an issue with the afpd conf:
/etc/netatalk/afpd.conf

I was using version 2 of the netatalk package and needed to specify 'uams_dhx2.so' instead of 'uams_dhx.so'. 

Like so:
- -transall -uamlist uams_randnum.so,uams_dhx2.so,uams_guest.so -nosavepassword -advertise_ssh

Note 'uams_guest.so' is for if you want guest access. See this for more info: [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#comment-48423](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#comment-48423)

Making that change and then restarting the netatalk daemon:
    sudo /etc/init.d/netatalk restart
got everything working. Hope that helps.

This solved the problem for me, thanks a million.

---

### Post by parisv on 2011-07-23
> **diff_sky said:**
> Hi,

I followed the tutorial at [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/) and got the same connection error.

It's possibly an issue with the afpd conf:
/etc/netatalk/afpd.conf

I was using version 2 of the netatalk package and needed to specify 'uams_dhx2.so' instead of 'uams_dhx.so'. 

Like so:
- -transall -uamlist uams_randnum.so,uams_dhx2.so,uams_guest.so -nosavepassword -advertise_ssh

Note 'uams_guest.so' is for if you want guest access. See this for more info: [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#comment-48423](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#comment-48423)

Making that change and then restarting the netatalk daemon:
    sudo /etc/init.d/netatalk restart
got everything working. Hope that helps.


I've been having the same problem thanks for this post!

---

### Post by rubicks on 2011-07-30
I've been having the same issue, but this fix doesn't work for me.  when i use this fix, instead of asking me for a username and password, it just try's to connect for a while and then gives it up.  its been working perfectly, then yesterday it just stopped working and i have no idea why...

---

