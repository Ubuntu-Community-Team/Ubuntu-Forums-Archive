---
title: "Mobile broadband connection"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by Sisophon2001 on 2009-08-01
In System->Preferences->Network Connections->Mobile Broadband->Add->Forward

Cambodia is not listed as an option.

One operator in Cambodia is Mobitel, and the correct connection options are;

Country code =kh 
Country name=Cambodia
Number is *99#
username: mobitel
password: mobitel
APN = cellcard

Is there some way to submit this to the database so it is included.

Thanks

Garvan

---

### Post by Sisophon2001 on 2010-06-02
These are the settings for Mfone.

3G Mobile settings for Mfone
Country code =kh
Country name=Cambodia
Number is *99#
username: <leave default>
password: <leave default>
APN = mfone

I think user name and password are always read from the sim, so the settings are ignored.

Now where should I submit this information so it gets added to the Ubuntu database?

Garvan

---

### Post by pdc on 2010-06-02
thanks for posting this

[https://launchpad.net/ubuntu/lucid/+source/mobile-broadband-provider-info/20100302-1](https://launchpad.net/ubuntu/lucid/+source/mobile-broadband-provider-info/20100302-1)

is the source file

can you have a read and work out how to notify these folks?

I see Onkar Shinde <email address hidden> is mentioned as being involved

____________

OK

when I click on this

[https://launchpad.net/ubuntu/+source/mobile-broadband-provider-info](https://launchpad.net/ubuntu/+source/mobile-broadband-provider-info)

more points of contact

---

### Post by alexfish on 2010-06-02
Hi

you can also look here

 [http://live.gnome.org/NetworkManager...vider_Database](http://live.gnome.org/NetworkManager...vider_Database)

you will need further details for the mmc and mnc numbers

details of how to find these can be found here

post #2

[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")




regards

alexfish

---

### Post by Sisophon2001 on 2010-06-02
> **alexfish said:**
> Hi

you can also look here

 [http://live.gnome.org/NetworkManager...vider_Database](http://live.gnome.org/NetworkManager...vider_Database)

you will need further details for the mmc and mnc numbers

details of how to find these can be found here

post #2

[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

regards

alexfish

Thanks for the information. I sent an email to the package maintainer.

Garvan

PS. I was too late to read alexfish's post, which shows the proper way to submit a patch. Thanks for the help.

---

