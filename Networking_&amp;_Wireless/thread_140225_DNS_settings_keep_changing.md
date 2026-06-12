---
title: "DNS settings keep changing"
date: 2006-03-05
forum: Networking &amp; Wireless
---

### Post by ssalman on 2006-03-05
Every time I reboot, I lose my DNS settings, I can change it back and it would work untill I reboot. I'm using a static IP setting, and have a wireless connection with WPA enabled, what is the problem? Thanks.

---

### Post by darth_vector on 2006-03-06
where do you make the change? you should list your DNS servers in /etc/resolv.conf

to do this you will have to edit the file as root```
sudo nano /etc/sources,list
```and put in something like this```
nameserver <ip of primary DNS>
nameserver <ip of secondary DNS>
```


give it a go and see if it sticks. as a last resort, you can put your DNS details directly in /etc/network/interfaces.

---

### Post by Lambert on 2006-03-06
If you're using static, you should list lines in your /etc/network/interfaces file for the dns server. NOt at my box right now to verify but you can look for more info in either 

man interfaces

or

/usr/share/doc/ifupdown/examples/network-interfaces

I can't remember exactly the second location and name but it's around there.

---

### Post by ssalman on 2006-03-06
Thanks darth_vector & Lambert for your help, I used both gui and cli to do this but without much luck, here is what I did:

gui, using the network manager added my router ip (192.168.2.1) in the DNS box
cli, I used the following comand as root:

echo nameserver 192.168.2.1 >> /etc/resolv.conf

as for the /etc/network/interfaces method I will give it a shot tonight. and will report results. thanks.

---

### Post by ssalman on 2006-03-06
Well I tried to add my DNS info to the /etc/network/interfaces file, but I didn't figure out how to add it, the man page did not include any options for DNS or NAMESERVER data, and the /usr/share/doc/ifupdown/examples/network-interfaces did not include any DNS info too

I may be missing a naming convension for the DNS/NamingServer that is not known to me! :)

Could you please help. Thanks.

---

### Post by darth_vector on 2006-03-07
you want something like this```
iface eth0 inet static
address 192...
netmask 255...
gateway 192...
dns-nameservers <ip>
```

---

### Post by Lambert on 2006-03-07
[quote=darth_vector]you want something like this```
iface eth0 inet static
address 192...
netmask 255...
gateway 192...
dns-nameservers <ip>
```[/quote] 
Just to add to darth_vector. You can add another line like this

```
dns-search ip3networks.com
```

---

### Post by ssalman on 2006-03-14
[FONT=Arial]Thanks Lambert & darth_vector for your help... I had to fix [another ]("http://www.ubuntuforums.org/showthread.php?t=140222")problem with my wireless card before I continue with this one... and now that I have it fixed I'm still trying to get this to work... I tried your solutions, but still the DNS setup keep on being reset after boot, what other configuration files affect the network setup, I think I may have changed a file while playing with the different settings to get my wireless to work and now it is taking [/FONT][FONT=&quot][FONT=Arial]precedence over my DNS setup??

Thanks.[/FONT] 
[/FONT]

---

