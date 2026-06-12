---
title: "help bring my samba back"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by orduek on 2011-10-29
Hi,
I have a mythbuntu 10.04 as a server. 
Until a week ago I had no problem connecting to my shared folders with another ubuntu machine using samba.
I don't really know what happend but I can't mount my samba folders anymore. I tried with two different computer.
When trying to mount the workgroup (MSHOME) I get an error message.
I attach the smbclient -L localhost (from the server)
```
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.4.7]
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: NT_STATUS_ACCESS_DENIED

``` 
Attached here is the sbmtree:
```
cli_start_connection: failed to connect to 192.168.0.154<20> (192.168.0.154). Error NT_STATUS_CONNECTION_REFUSED
cli_start_connection: failed to connect to HTPC<20> (192.168.0.154). Error NT_STATUS_CONNECTION_REFUSED

```

attached is my smb.conf of the server:
```
[global]
	workgroup = MSHOME
	server string = %h server (Samba, Mythbuntu)
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	dns proxy = no
	security = share
;	encrypt passwords = yes
;	guest ok = yes
;	guest account = nobody
;	guest ok = no

[recordings]
	comment = TV Recordings
	path = /var/lib/mythtv/recordings
	public = yes
;	writable = No
	create mask = 0777
	directory mask = 0777
	force user = nobody
	force group = nogroup

[videos]
	comment = Videos
	path = /var/lib/mythtv/videos
	public = yes
	writable = yes
	create mask = 0660
	directory mask = 0770
	force user = mythtv
	force group = mythtv

[music]
	comment = Music
	path = /var/lib/mythtv/music
	public = yes
	writable = yes
	create mask = 0660
	directory mask = 0770
	force user = mythtv
	force group = mythtv

[pictures]
	comment = Pictures
	path = /var/lib/mythtv/pictures
	public = yes
	writable = yes
	create mask = 0660
	directory mask = 0770
	force user = mythtv
	force group = mythtv

[music-1]
	path = /storage/media/Old_Mythtv/music
	writeable = yes
;	browseable = yes
	guest ok = yes
```

Can someone help me please?

---

