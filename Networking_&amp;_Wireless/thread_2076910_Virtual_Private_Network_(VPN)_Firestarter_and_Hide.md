---
title: "Virtual Private Network (VPN) Firestarter and Hidemyass"
date: 2012-10-27
forum: Networking &amp; Wireless
---

### Post by mtn on 2012-10-27
Hi, I just started using the web proxy service Hidemyass. I have set up the vpn connection in "Network Connections", however, I only get a successful connection if I stop the firewall with Firestarter. I have read lots and lots of forum threads and tried lots of different settings but every time I start the firewall the connection drops and every time I stop the firewall it works! I just can't find accessible information regarding how to set-up Firestarter to let the vpn connection through.

My current set-up in Firestarter is:

In the "Policy" tab > "Inbound traffic policy" >  "Allow connections from host" > [my vpn IP address]

In the "Policy" tab > "Inbound traffic policy": 
```
Allow service: unknown
Port: 1723
For: my vpn IP address]
```

In /etc/firestarter/user-pre (i.e., $ ```
sudo gedit /etc/firestarter/user-pre
```) I am using the following settings.

```
 # Forward PPTP VPN client traffic
$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $INIF -o $IF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
```

I'm really stuck with this. Any help would be really appreciated.

[edit] I'm using, fully updated, Ubuntu 12.04 [end edit]

---

### Post by FrankT-Qc on 2012-10-27
Unfortunately, firestarter is for simple setups and doesn't always offer the options to work with elaborated network setup. Nevertheless, firestarter merely generates scripts to configure NetFilter (iptables).

If you look in the folder /etc/firestarter, you'll have access to the scripts that firestarter generates. If you look at them, you will realise that it does not like when "Internet" comes from more than one path.

More importantly, you'll have a few "post" scripts where you could had a few tweaks to complete your firewall setup beyond what the graphical interface allows you...

welcome to iptables; it's cold for the first few minutes, but if you keep the man page on the side, it's pretty easy to come up with a very good/simple setup.

---

### Post by mtn on 2012-10-27
Hi Frank,

Thanks for your reply. Okay, so I will go and look at a few tutorials about iptables and try and warm up to the topic!

I was just reading this thread [http://askubuntu.com/questions/22667/why-is-the-firewall-disabled-by-default/22736](http://askubuntu.com/questions/22667/why-is-the-firewall-disabled-by-default/22736) It helped me to understand the concepts a bit better.

I got rid of Firestarter (purged it i.e., deleted it and all configuration files, rather than just removing it. Code: ```
sudo apt-get purge firestarter
```) And installed gufw (gui for ufw, which is it's self an application that one can use to manipulate iptables - as I understand it!).

With Firestarter gone and ufw turned ON using gufw my VPN seems to work fine!!! I'm guessing ufw configures iptables differently by default and must allow (open!) the port the VPN uses... more research into iptables is necessaries... though from what I have read... unless I'm using a public wifi connection (i.e., a connection that is not behind a router/hardware-firewall and on a network I don't trust) then I should be fine whatever my set-up! So for example, I'm safe on my home network because I'm behind my router's firewall and connecting over my encrypted WAP signal, and, I'm also safe connecting to the internet at my parents house because I trust the other computers on the network and again I'm behind their router and using an encrypted signal. I guess if, say, my dad's Windows computer was compromised then someone could attack my computer on their network through his computer! But then, I have got my folks on Ubuntu now so it should all be pretty safe!

Sunny here :) Thanks

---

### Post by pattinsonbvs on 2012-12-27
before few days i am very confused which one is best vpn provider but i finally read the reviews of more than 10 vpn provider tha best review is Hidemyass (HMA) thats why i finally select HMA Vpn service if anyone Read [HIDEMYASS REVIEW]("http://www.bestvpnservice.com/blog/hidemyass-review/") go here

---

