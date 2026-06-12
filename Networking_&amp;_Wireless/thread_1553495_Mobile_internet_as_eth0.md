---
title: "Mobile internet as eth0"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by Otu on 2010-08-15
So, is it possible to set mobile internet as eth0?
the reason for this is that etherape and wireshark wont recognize/work with my mobile internet.

---

### Post by Kerubu on 2010-08-15
Assuming when you say mobile internet, you mean a USB dongle:

Your connection from your dongle to the mobile network is point-to-point so if you're wanting to see what's being sent along that point-to-point path you're using the wrong tool. wireshark and the like only work (as far as I know) on local networks where you have multiple machines sharing one network.

Effectively all you want to do is see what data is flowing in and out of the USB port, not monitor what is happening on ethernet.

---

### Post by Kerubu on 2010-08-15
Opps.. I possibly stand corrected:

[http://wiki.wireshark.org/CaptureSetup/NetworkMedia]("http://wiki.wireshark.org/CaptureSetup/NetworkMedia")

---

### Post by Otu on 2010-08-15
Yes i mean usb dongle with simcard and all.. also wireshark and the like work on other than local network, unless you count the whole internet as local?

i just found this on wireshark wiki:
On Linux, you won't be able to capture PPP control protocol traffic in the usual manner (via libpcap) as that traffic is not supplied to the networking stack. You will be able to capture IP traffic, for example, but you won't be able to see the PPP headers, as the PPP code doesn't supply them to the networking stack.

The PPP control protocol traffic can be captured by configuring the ppp daemon to 'record' to a capture file all the data the daemon sends and receives. Wireshark can then be used to display the created capture file.

On Fedora Core 6 the pppd capture file is created if 'record filename-of-your-choice' is added as a line in /etc/ppp/options (YMMV: see 'man pppd').

Note that all traffic on the PPP port is captured to the file so this option, if left on, may cause a large capture file to be generated.


must be some way to do this.. some virtual modem thingie.. cmon, someone here has to know how?

or atleast some software that can do what they describe in the wiki, to record some traffic in a file.

---

