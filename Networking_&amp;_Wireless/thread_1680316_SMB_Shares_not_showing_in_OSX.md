---
title: "SMB Shares not showing in OSX"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by Saidear on 2011-02-02
I am using Ubuntu as a file server, and recently my SMB shares stopped showing up.  I think Avahi is the cause.

Network topology is simple:

192.168.1.1 = Router
192.168.1.100-149 = DHCP reserved for clients
192.168.1.150 = Server (named "Athena" in all relevant hosts files to make it easier)

I created the following in etc/avahi/services/samba.service:

```
<?xml version="1.0" standalone='no' ?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">

<service-group>
	<name replace-wildcards="yes">%h filer</name>
	<service>
		<type>_smb._tcp</type>
		<port>139</port>
		<host-name>athena</host-name>
	</service>
	<service>
		<type>_device-info._tcp</type>
		<port>0</port>
		<txt-record>model=XServe</txt-record>
	</service>
</service-group>
```

And nothing shows up on my MacBook

The AFP version of the same service (afpd.service), if I do that.. and it shows up instantly.  I don't really want to go through configuring the AFP service and just want to use SMB as I have Windows machines that also access this server.

Is there something I'm missing or doing wrong?

---

