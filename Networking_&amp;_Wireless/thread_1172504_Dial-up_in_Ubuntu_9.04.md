---
title: "Dial-up in Ubuntu 9.04"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by teking66 on 2009-05-28
How do I setup a dail-up connection in Ubuntu 9.04 Desktop?

 I installed from the free CD and the only way I can currently connect to the internet is to boot up into Windows. I would like to be able to connect from inside Ubuntu.

---

### Post by nakedfanatic on 2009-05-28
The Dial-up modem you have is probably a "soft modem". These rely on proprietary drivers (usually Windows only) to run. Linux versions of these drivers can be difficult or impossible to find, and often are not free.

An older style of modem known as a "hardware" modem does not require any drivers and work straight away in Linux. These modems are external and connect to your computer via its serial port. I don't think the more modern USB external modems would work.

When I had the same problem I found an external modems second-hand for a very cheap price, and it worked! :p This would probably be your best option too.

You could try searching for linux drivers for your modem, but in my experience this is the painful option.

Ian.

---

### Post by teking66 on 2009-05-28
Yea, my modem is a soft modem, and I have installed the driver for it. Everything went fine there, at least from the text output in the console window.

My problem is that I am not finding a ppp GUI, kppp nor gnome-ppp are installed. They are not on the disk either. So, you see, I am in a catch 22 here. I need to get to the internet to get what I need, but I can't get to the internet to get what I need.

Now, I am wondering why would one of these applications not be included on the CD?

If I am missing something here then would someone please tell me what or how to get there.

---

### Post by nakedfanatic on 2009-05-28
You can configure and use your modem from the command line until you can get a gui installed.

Some step-by-step instructions are here: [http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)

You will need to use wvdialconf and wvdial. (remember to put 'sudo' in front of these commands.

---

### Post by teking66 on 2009-05-31
I had to download WVDial, Gnome-ppp and a few required packages thru windows.
But, I have it working now.

Thanks to all for your replies.

---

