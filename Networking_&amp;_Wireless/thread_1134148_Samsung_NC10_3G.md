---
title: "Samsung NC10 3G"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by cmistake on 2009-04-23
Hi.

After installing Jaunty my 3G connection went unstable. It works right out of the box and it works well, but after some time, anything from a minute to half an hour, it disconnect, and connects again only after rebooting. It just stops transferring data and then it says GSM network disconnected, and when I try to reconnect it, it tries to connect for about ten seconds and then it just says that the GSM network is disconnected. 

It worked perfectly in 8.10 with an unofficial update, that seems to have been included in 9.04, but now it just keeps failing. It did the same thing in Beta, but I lived with it becouse of the beta state. Now I'm looking for help.

I've tried "sudo /etc/init.d/NetworkManager restart", as it's been a big help with problems in networking, but it doesn't help me now.

I'm not expecting anyone to have a solution ready, but any help is welcome. For example command line connecting where the problem could be seen or some logs that tell me about networking. At this point an error message would be welcome, so I would have something to work with :)

---

### Post by cmistake on 2009-04-24
bump

---

### Post by cmistake on 2009-04-30
When I kill nm-applet and start it from command line this is what I get

```
** (nm-applet:28864): DEBUG: applet_common_device_state_changed
** (nm-applet:28864): DEBUG: old state indicates that this was not a disconnect 1
** (nm-applet:28864): DEBUG: applet_common_device_state_changed
** (nm-applet:28864): DEBUG: old state indicates that this was not a disconnect 2
** (nm-applet:28864): DEBUG: applet_common_device_state_changed
** (nm-applet:28864): DEBUG: foo_client_state_changed_cb


```

At this point I try to connect to my 3g 
> 
** (nm-applet:28864): DEBUG: foo_client_state_changed_cb
** (nm-applet:28864): DEBUG: going for offline with icon: notification-gsm-disconnected
** (nm-applet:28864): DEBUG: applet_common_device_state_changed
** (nm-applet:28864): DEBUG: old state indicates that this was not a disconnect 9
** (nm-applet:28864): DEBUG: going for offline with icon: notification-gsm-disconnected


This doesn't help me. It might help me if I knew what handles the network other than NetworkManager and nm-applet. Some module or something that I could remove and probe back to get my connection working without a reboot.

---

### Post by cmistake on 2009-04-30
For anyone having similar problems, the bug seems to be in cdc-acm driver. After probing it off and back on I was able to get my network to work again. 

Here's the command

```
sudo modprobe -r cdc-acm
sudo modprobe cdc-acm
```

Hope it helps.

---

### Post by flittermice on 2011-05-30
Yes, this helps.
Even under Ubuntu 10.10...

Thanks very much!

---

