---
title: "Hostname and DHCP"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by m_2009 on 2009-05-11
Can anyone tell me how to force ubuntu to send the hostname to DHCP/DNS.

I have edited the etc/dhcp3/dhclient.conf file and made sure the send host-name "<hostname>"; line is uncommented, and even changed the values to various hostnames, however when i log into my netgear router and look in the DHCP table or currently attached devices my ubuntu machine shows up as "UNKNOWN"

Is tehre anyway to solvethis problem?

---

### Post by Iowan on 2009-05-11
:confused:  My */etc/dhcp3/dhclient.conf * file has a line:```
send host-name "DELL4100";
```The DHCP server has entries:```
lease 192.168.1.11 {
  starts 0 2009/05/10 20:27:46;
  ends 0 2009/05/17 20:27:46;
  tstp 0 2009/05/17 20:27:46;
  binding state active;
  next binding state free;
  hardware ethernet 00:1e:da:b0:f8:bd;
  client-hostname "DELL4100";
}
```My DHCP server is a Breezy Ubuntu box.

---

### Post by m_2009 on 2009-05-19
MY netgear shows my ubuntu meachin as UNKNOWN, yet displays the ip address.

Also even with samba installed, windows machines are not able to access the ubuntu machine by host name, only by IP address.

Why does ubuntu seem to have such difficulties communicating on networks with other machines and DHCP etc??

And why by default doesnt ubuntu send host name?

---

### Post by Iowan on 2009-05-19
Just my opinion - but Ubuntu seems to be security-minded.  Better to let the user open up what (s)he wants, than try to figure out what to close if (s)he doesn't want. Ubuntu comes with several clients pre-installed... but to allow access to the machine usually requires installing a server package.

---

### Post by m_2009 on 2009-05-19
Its not even about accessing the machine. Its about the machine being visible as part of the actual network, instead of not even being able to be seen as connected to the network....
 
In windows you can choose wether or not to allow access to the machine, and even disable file sharing all together, yet the machine still shows up in the network by its proper host name...

---

