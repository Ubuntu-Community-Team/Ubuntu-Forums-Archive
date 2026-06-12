---
title: "Problems with Synaptic Network connections"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by Ahnab on 2011-02-28
Hi! I'm a kinda newbie with Ubuntu and so far love it!

I'm using 10.10 on a 64-bit machine, and the problem I've got is that, although my internet connection's working perfectly (just downloaded Blender), my Synaptic (and all other update managers, for that matter) fail to run any updates, saying that they're experiencing network connectivity issues.

Would appreciate any/all help you guys can throw my way. Thanx!

---

### Post by An Sanct on 2011-02-28
Run the update manager

System > Administration > Update Manager

Click "Settings" in the left bottom corner, select the "Ubuntu Software" tab and from the "Download from:" dropdown, select "Other..."

Then in the "Choose a Download Server" hit the button "Select Best Server".

This will pick the best performing server from the global list.

---

### Post by Ahnab on 2011-02-28
[LEFT]I did as you said. It scrolled through the entire server list and in the end gave me prompt saying: "No suitable download server was found. Please check your internet connection."

The problem is that my net's working just fine (I'm browsing and downloading stuff without any issues). Any idea whats goin on?
[/LEFT]

---

### Post by An Sanct on 2011-02-28
That's weird... could you please post the result of ifconfig? Sounds to me like there is something wrong with your IP settings ...

---

### Post by Ahnab on 2011-02-28
Ok, this is what I get:-

th0      Link encap:Ethernet  HWaddr 00:1c:c0:b0:69:69  
          inet addr:172.20.12.67  Bcast:172.20.15.255  Mask:255.255.252.0
          inet6 addr: fe80::21c:c0ff:feb0:6969/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:286525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:278848148 (278.8 MB)  TX bytes:18402149 (18.4 MB)
          Interrupt:20 Memory:d3300000-d3320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9858 (9.8 KB)  TX bytes:9858 (9.8 KB)

Hope it makes sense 'coz I sure don't know what the heck's goin on! :-p Again, thanx for all the help!

---

### Post by An Sanct on 2011-02-28
1. Are you on a DHCP setup or did you input the IPs manually?
2. Are you using IPv6? (is ipv6 Settings set to 'ignore')

---

### Post by Ahnab on 2011-02-28
1.  Manual input of IP's (IPv4)
2.  IPv6 is set to ignore

---

### Post by An Sanct on 2011-02-28
That's strange ... if browsing the net works okay, updates should too!

What do you see as a result of:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Ahnab on 2011-02-28
Ya I know, bloody strange. :-(

Ok, I ran the commands you said and I get a whole slew of lines like:-

Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick Release.gpg
Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                  
  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (113: No route to host)
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
  Unable to connect to archive.canonical.com:http:
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US
  Unable to connect to archive.canonical.com:http:
Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                  
  Unable to connect to archive.canonical.com:http:
Err [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en      
  Unable to connect to archive.canonical.com:http:
Err [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_US   
  Unable to connect to archive.canonical.com:http:
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release                      
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release                      
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources               
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages        
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages        
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources               
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages        
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages        
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources               
  Unable to connect to archive.canonical.com:http:
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages        
  Unable to connect to archive.canonical.com:http:
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages        
  Unable to connect to archive.canonical.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                       
  Could not connect to extras.ubuntu.com:80 (91.189.88.33). - connect (113: No route to host)
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en       
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
  Unable to connect to extras.ubuntu.com:http:
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages
  Unable to connect to extras.ubuntu.com:http:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (113: No route to host) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted amd64 Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/ maverick/main Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/ maverick/main Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/ maverick/restricted Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/ maverick/restricted Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick/main amd64 Packages/DiffIndex
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick/restricted amd64 Packages/DiffIndex
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (113: No route to host) [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (113: No route to host)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to extras.ubuntu.com:80 (91.189.88.33). - connect (113: No route to host)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.canonical.com/dists/maverick/Release.gpg](http://archive.canonical.com/dists/maverick/Release.gpg)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en.bz2)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-amd64/Packages.gz)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://archive.canonical.com/dists/maverick/partner/binary-amd64/Packages.gz](http://archive.canonical.com/dists/maverick/partner/binary-amd64/Packages.gz)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.40 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.


Hope this makes sense.

---

### Post by Ahnab on 2011-03-01
Help! Anyone! Please!

---

### Post by An Sanct on 2011-03-01
if you click on this link (from your post above), does it give you "Packages.gz" to download/save?

[http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz)

---

### Post by Ahnab on 2011-03-01
Yeah, I get the download/save prompt.

---

### Post by Ahnab on 2011-03-01
I get the prompt nad even manage to download the package.

---

### Post by Ahnab on 2011-03-01
Anyone figure this out please? Its bloody driving me insane!

---

### Post by eklikeroomys on 2011-05-27
Im having the exact same problem, I guess it has something to do with static IP or DNS server but I have tool little experience to fix the problem.

---

### Post by baalkikhaal on 2011-07-16
I am facing a similar problem. Proxy and IP settings are working fine for browsing the net, but synaptic is unable to fetch repositories.

I have used Network Manager to set my Prixy and IP. It is surprising that it doesnt edit /etc/network/interfaces file. My question is where is the information for IP,netmask,gateway stored in this case. I did not have success manually configuring the network

**ifconfig output** is

```
  
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:a9:14:98  
          inet addr:10.7.32.81  Bcast:10.7.63.255  Mask:255.255.224.0
          inet6 addr: fe80::beae:c5ff:fea9:1498/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17549 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12349118 (12.3 MB)  TX bytes:1892591 (1.8 MB)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5871 (5.8 KB)  TX bytes:5871 (5.8 KB)


```[B]

/etc/apt/sources.list reads

[/B]```
  
deb [ftp://ftp.iitb.ac.in/os/ubuntu/archives/](ftp://ftp.iitb.ac.in/os/ubuntu/archives/) maverick main
deb-src [ftp://ftp.iitb.ac.in/os/ubuntu/archives/](ftp://ftp.iitb.ac.in/os/ubuntu/archives/) maverick main

```**/etc/environment **gets edited after network manager configures the IP and proxy

```
  
http_proxy="http://netmon.iitb.ac.in:80/"
ftp_proxy="ftp://netmon.iitb.ac.in:80/"
https_proxy="https://netmon.iitb.ac.in:80/"

```**synatic error** message is 
```
  
Failed to fetch ftp://ftp.iitb.ac.in/os/ubuntu/archives/dists/maverick/Release.gpg  
Failed to fetch ftp://ftp.iitb.ac.in/os/ubuntu/archives/dists/maverick/main/i18n/Translation-en.bz2  
Failed to fetch ftp://ftp.iitb.ac.in/os/ubuntu/archives/dists/maverick/main/i18n/Translation-en_US.bz2

```

---

### Post by baalkikhaal on 2011-07-17
i think my problem is with trying to use apt-get behing a proxy server. I searched for this and found 

[http://raetsel.wordpress.com/2006/10/29/laptop-build-apt-get-behind-a-proxy](http://raetsel.wordpress.com/2006/10/29/laptop-build-apt-get-behind-a-proxy)

relevant. Will post later if this works out

---

### Post by baalkikhaal on 2011-07-17
> **Ahnab said:**
> 1.  Manual input of IP's (IPv4)
2.  IPv6 is set to ignore

Hi 
Did you solve your problem. If so could you be kind to tell what did you do to make synaptic work

If not, my question is do you connect via a proxy server. Because if that is the case your problem is similar to mine. Post what 

```
sudo gedit /etc/environment
```gives in the /etc/environment file

This link might be useful 
[http://raetsel.wordpress.com/2006/10/29/laptop-build-apt-get-behind-a-proxy/](http://raetsel.wordpress.com/2006/10/29/laptop-build-apt-get-behind-a-proxy/)

---

