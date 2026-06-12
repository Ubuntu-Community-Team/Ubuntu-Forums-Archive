---
title: "Networking Pc ,Xbox ,Router"
date: 2006-01-12
forum: Networking &amp; Wireless
---

### Post by M3lted on 2006-01-12
Hey there
im trying to set up my litle network here , but it wont work .
the router is a modem and router in 1 from my isp.
here's the Setup.

```

                
internet-----Router/Modem----Pc1-------Xbox360
             |----------Pc 2    


```

Now everthing is configured to get an Ip via dhcp.
So pc1 and Pc2 get there ip no probs there
In pc 1 i got 2 NiC's 
Eth0 = has the internet connection,and works fine
Eth1 = the xbox that should get an ip via dhcp ,but this doesnt happen

iv been trying it with static ip's and eth0 als gateway but that dont work 
i know this setup should work bc it always been like that in winblows , but for some weird reason  it wont work in ubuntu:(

so all tip's and hint's are welcome :)

---

### Post by woedend on 2006-01-13
why go to the pc first?  rout it to the xbox.

---

### Post by M3lted on 2006-01-13
[QUOTE=woedend]why go to the pc first?  rout it to the xbox.[/QUOTE]

Wel tried that to but it didnt got an ip :S ,i even rebooted the router/modem but nogo :(

---

### Post by Peter76 on 2006-01-13
To share the internet connection to your xbox, install firestarter on pc1 ( sudo apt-get install firestarter ) and turn on the connection sharing. If you want the xbox configured through dhcp, you have to run a dhcp-server on pc1 as well... But it's easiest to give it a static ip.

Good luck

---

### Post by M3lted on 2006-01-13
I do have firestarter, and dhcp3-server but it fails to load or work properly.
so i removed it .
Then i pulled out all the network cables from the router/modem and only plugged the xbox in ,rebooted router/modem plugged the other pc's in router and go go

---

