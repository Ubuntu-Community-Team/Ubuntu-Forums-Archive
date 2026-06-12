---
title: "Canon imageCLASS D480 network scanning..."
date: 2012-03-04
forum: Networking &amp; Wireless
---

### Post by opgenorth on 2012-03-04
I've been beating my head against my Canon imageCLASS D480 for a couple of days now.  I've got the printer working over the network, but can't get the scanner to work.  I'm running Ubuntu 10.10 64bit and have compiled the latest sane-backends 1.0.23 and edited /etc/sane.d/pixma.conf adding the line "bjnp://192.168.11.xxx.xxx" (printer is configured with a static ip)

When I run xsane from a terminal I get:
 
[pixma] udp_command: no data received (recv): Connection refused[pixma] udp_command: no data received (recv): Connection refused[pixma] udp_command: no data received (recv): Connection refused[pixma] Cannot read scanner make & model: &#65533;&#65533;

in the terminal window (at the very end there are 0 to 4 seemingly random characters, most unprintable), while the xsane window says "scanning for devices" then the xsane window changes to "no devices available"


So, my best guess is that the backend is trying to connect to the scanner, but can't understand the reply that it's getting.  FWIW, if I comment out the "bjnp://192.168.11.xxx.xxx" line, then xsane just scans for devices and doesn't find them but the terminal does not show any of the previous "[pixma] udp_command: no data received (recv):"....  The computer and the scanner are on the same subnet.

Any suggestions of what to try next?

---

### Post by dongwoo17 on 2012-05-17
How did you get to make network (or even USB) printing work? (Sorry I know less than you do...)

I downloaded the linux drivers from canon site, used alien to change rpm's to deb's and installed them using ubuntu software center.

Then I went to Printing and installed my D480, going through series of dialogs.... but when I printed the test page, it won't print... Could you help? I tried installing it as USB as well as Network Printer.

---

### Post by DaneM on 2012-08-17
I believe the solution to your problem is here:

[http://ubuntuforums.org/showpost.php?p=12089554&postcount=99](http://ubuntuforums.org/showpost.php?p=12089554&postcount=99)

You'll need to follow the instructions on posts #99, 103, and 104.  These assume you're using 64-bit Ubuntu (or Mint); if you're using 32-bit, then you can skip many of the steps.  After months of banging my head against the wall, we were able to collectively solve the printing problem.

Now to get scanning working...

---

