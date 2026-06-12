---
title: "Bluetooth Tethering In Jaunty Versus Windows XP"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by Windows Refugee on 2010-01-21
I have both Jaunty and Windows XP installed on my laptop (dual boot), and I have successfully tethered (via Bluetooth) my cellphone in Windows, but can't get tethering to work in Jaunty.

In Windows, when I paired my phone with my laptop using Bluetooth, Windows assigned two COM ports for Bluetooth to use.  Then I configured dial-up networking, and all I had to specify was the dial string (*99**1*1#). Windows treats my cellphone as if it were a modem connected via a serial port.  Works great.

When I pair my phone to the laptop when running Jaunty, I don't ever see serial ports getting configured as I do in Windows.  And I've read that when the Bluetooth pairing takes place in Ubuntu, the networking wizard should start, but it does not.  So, I go into network connections and create a new connection under the MOBILE BROADBAND tab (I check "connect automatically").  When I'm finished creating the connection, it says "never" to the right of the connection name, but I'm not sure what that is indicating.  When I left-click the network manager icon on my desktop, it does not show any connections from which I can choose. I have no Internet connectivity.

I have proved that the Bluetooth link between Jaunty and my cellphone IS working.  I have been successful sending files from my phone to Jaunty, using Bluetooth.

Am I going about setting up tethering incorrectly ?

---

### Post by Windows Refugee on 2010-01-22
I have also tried the following without any luck...

sudo aptitude install bluez-compat
hcitool scan  (which did indeed find my phone's MAC address)
sudo pand --connect <mac addr> -n  (reported "connection refused")
sudo dhclient bnep0   (I didn't get this far)


Any ideas ?

---

### Post by Windows Refugee on 2010-01-23
Does anyone know if some cellphones can't support PAN ?  I am using a Samsung SGH-G600.  Is it possible that it's firmware supports dialup networking, but not joining a PAN ?

As I posted, it pairs with my laptop's bluetooth when I boot with Windows XP, and gets two serial ports assigned.  Then, I can set up dialup networking (DUN) between Windows and the phone.  But as I've indicated, when I try PAND in Ubuntu, it reports "Connection Refused".

Also, can serial ports be associated with a bluetooth pairing in Ubuntu, the way they are in Windows ?

---

