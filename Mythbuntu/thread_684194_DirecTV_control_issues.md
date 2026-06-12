---
title: "DirecTV control issues"
date: 2008-01-31
forum: Mythbuntu
---

### Post by Rhiadon on 2008-01-31
I have installed the directv.pl script in /usr/local/bin. I can run this script from the command line as root and the channel changes as I would expect. 
I have placed the following line in the external channel change command line in the backend setup:
/usr/local/bin/directv.pl port /dev/ttyS0 box_type H20 setup_channel

Also:

/usr/local/bin/directv.pl port /dev/ttyUSB0 box_type H20 setup_channel

This is because I have two directv receivers. Both of those exact lines will work from the command line as root. The mythbackend is running as root.

The error I see in the log is as follows:

ChannelBase: external tuning program exited with error 255

I imagine there is a way to do some more logging but I'm currently recording Lost so I'm not shutting the backend down right now. :)

So does anybody have any idea what I need to do to fix this?

Thanks.

---

### Post by hoyer801 on 2009-03-19
Did you ever find the resolution to this? I'm having the exact same problem.

---

### Post by Rhiadon on 2009-03-20
Now I wish I'd kept better notes because this was a while ago. I'm guessing that what I dis was the chmod 777 the script and it worked. I'm not certain of that though. Sorry man.

---

