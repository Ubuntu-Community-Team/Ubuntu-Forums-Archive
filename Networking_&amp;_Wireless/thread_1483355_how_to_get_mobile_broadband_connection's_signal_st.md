---
title: "how to get mobile broadband connection's signal strength?"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by hemlockz on 2010-05-14
Hi all,
 
Is there a way to list 3g connection signal strength with network-manager or modem-manager from the command line? I have the latest network-manager and 10.04 NBR. I want to be able to script a job to send connection signal strength every few minutes from my remote laptop.

---

### Post by alexfish on 2010-05-14
hi

for modem manager look here / copy and paste the link to your browser

[file:///usr/share/doc/modemmanager/spec.html](file:///usr/share/doc/modemmanager/spec.html)

regards

alexfish

---

### Post by hemlockz on 2010-05-14
Thanks, I have that documentation up but how do I access these methods?  Its a dbus interface specification.. but how do i access those methods through command line?  "modem-manager quality" doesn't return anything

---

### Post by alexfish on 2010-05-14
hi

just tried to access , got message back

modem-manager: Could not acquire the org.freedesktop.ModemManager service.#012  Message: 'Connection ":1.138" is not allowed to own the service "org.freedesktop.ModemManager" due to security policies in the configuration file'

PAH

may a ppp script with loop in to send AT+CSQ would be easier?

or get modem manager to give permissions 

good luck

---

### Post by foresthill on 2010-05-14
This might not be quite what the OP is looking for, but I use the System / Administration / System Monitor applet while I'm downloading and just keep an eye on my download rate in that.

If you mean signal strength, as in number of bars like on a cell phone, I personally use the illuminated bars on the side of my broadband modem. But that's not terribly useful, since the number of people on the network at any given time determines how much bandwidth I can get much more so than the signal strength. 

Are you trying to improve your reception by looking at what spot in the house you get the best signal? What is it exactly you are trying to do?

---

### Post by hemlockz on 2010-05-14
Its for a remote laptop that I leave in the field for days at a time. I use to capture wireless traffic.  The mobile broadband connection allows me to send a request to my web server every 15 minutes with the size of my capture files.  Like a health checkup.  My webserver then just posts that to a text file as soon as the GET request comes in, that I can pull up by going to my server and clicking on the text file from any web browser or phone.  Doing this lets me know my laptop is still working, and the captures are still growing at a consistent rate, meaning nobody ripped down my antennas.... So in addition to capture file size, I would also like to send to my server the broadband connection's signal strength... it changes depending on weather.  If I can monitor signal quality along with my filesize, it would be nice.  So if my signal quality get progressively lower at one station that eventually stops reporting back, I can likely assume its a signal strength/quality problem, and there is a good chance I do not need to visit the remote machine, just wait until the weather improves and it reconnects.  but if I stop getting reports back from a machine that was reporting good signal strength anyway, I may in that case want to run out and check on it.  ... cool, huh?  BTW I am not haking or stealing personal information, its a work project trying to implement anonymous MAC address tracking between two different capture points.

---

