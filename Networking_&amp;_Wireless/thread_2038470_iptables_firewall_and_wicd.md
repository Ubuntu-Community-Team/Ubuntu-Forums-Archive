---
title: "iptables firewall and wicd"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by jhmgbl on 2012-08-06
Hallo,

I installed a generated firewall script, but now wicd does no more connect to my router via wlan0. I have to switch off the firewall, wait until wicd connects and then start the firewall again. Which ports do I have to open? Here is my script:


  ```
  # alle Regeln löschen
      $iptables -t nat -F
      $iptables -t filter -F
      $iptables -X
    
      # neue Regeln erzeugen
      $iptables -N garbage
      $iptables -I garbage -p TCP -j LOG --log-prefix="DROP TCP-Packet: " --log-level info
      $iptables -I garbage -p UDP -j LOG --log-prefix="DROP UDP-Packet: " --log-level info
      $iptables -I garbage -p ICMP -j LOG --log-prefix="DROP ICMP-Packet: " --log-level info

      # Default Policy
      $iptables -P INPUT DROP
      $iptables -P OUTPUT DROP
      $iptables -P FORWARD DROP



      # über Loopback alles erlauben
      $iptables -I INPUT -i lo -j ACCEPT
      $iptables -I OUTPUT -o lo -j ACCEPT

      #####################################################
      # ausgehende Verbindungen
      #iptables -N whitelist
      #iptables -A whitelist -s 192.168.178.0/24 -j ACCEPT
      #iptables -A whitelist -t filter -s 183.98.143.10/24 -j ACCEPT
      # Port 22
      $iptables -I OUTPUT -o wlan0 -p TCP --sport 1024:65535 --dport 22 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      $iptables -I INPUT -i wlan0 -p TCP --sport 22 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
      # Port 53
      $iptables -I OUTPUT -o wlan0 -p TCP --sport 1024:65535 --dport 53 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      $iptables -I INPUT -i wlan0 -p TCP --sport 53 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
      $iptables -I OUTPUT -o wlan0 -p UDP --sport 1024:65535 --dport 53 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      $iptables -I INPUT -i wlan0 -p UDP --sport 53 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
      # Port 80
      $iptables -I OUTPUT -o wlan0 -p TCP --sport 1024:65535 --dport 80 -m state --state NEW,ESTABLISHED,RELATED --match set --set whitelist dst -j ACCEPT
      $iptables -I INPUT -i wlan0 -p TCP --sport 80 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Port 443
      $iptables -I OUTPUT -o wlan0 -p TCP --sport 1024:65535 --dport 443 -m state --state NEW,ESTABLISHED,RELATED --match set --set whitelist dst -j ACCEPT
      $iptables -I INPUT -i wlan0 -p TCP --sport 443 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT 
# Port 8080
      #$iptables -I OUTPUT -o wlan0 -p TCP --sport 1024:65535 --dport 8080 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      #$iptables -I INPUT -i wlan0 -p TCP --sport 8080 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
      # Port 3128
      #$iptables -I OUTPUT -o wlan0 -p TCP --sport 1024:65535 --dport 3128 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      #$iptables -I INPUT -i wlan0 -p TCP --sport 3128 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
            
# ICMP
      $iptables -I OUTPUT -o wlan0 -p ICMP --icmp-type echo-reply -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      $iptables -I INPUT -i wlan0 -p ICMP --icmp-type echo-reply -m state --state ESTABLISHED,RELATED -j ACCEPT

      #####################################################
      # eingehende Verbindungen
      # Port 22
      $iptables -I INPUT -i wlan0 -p TCP --sport 1024:65535 --dport 22 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      $iptables -I OUTPUT -o wlan0 -p TCP --sport 22 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
      # Port 53
      $iptables -I INPUT -i wlan0 -p TCP --sport 1024:65535 --dport 53 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      $iptables -I OUTPUT -o wlan0 -p TCP --sport 53 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
      $iptables -I INPUT -i wlan0 -p UDP --sport 53 --dport 53 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      $iptables -I OUTPUT -o wlan0 -p UDP --sport 53 --dport 53 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      $iptables -I INPUT -i wlan0 -p UDP --sport 1024:65535 --dport 53 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      $iptables -I OUTPUT -o wlan0 -p UDP --sport 53 --dport 1024:65535 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      # Port 80
      $iptables -I INPUT -i wlan0 -p TCP --sport 1024:65535 --dport 80 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      $iptables -I OUTPUT -o wlan0 -p TCP --sport 80 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Port 443
      $iptables -I INPUT -i wlan0 -p TCP --sport 1024:65535 --dport 443 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      $iptables -I OUTPUT -o wlan0 -p TCP --sport 443 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
      # Port 8080
      #$iptables -I INPUT -i wlan0 -p TCP --sport 1024:65535 --dport 8080 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      #$iptables -I OUTPUT -o wlan0 -p TCP --sport 8080 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
      # Port 3128
      #$iptables -I INPUT -i wlan0 -p TCP --sport 1024:65535 --dport 3128 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      #$iptables -I OUTPUT -o wlan0 -p TCP --sport 3128 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
            
# ICMP
      $iptables -I INPUT -i wlan0 -p ICMP --icmp-type echo-request -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
      $iptables -I OUTPUT -o wlan0 -p ICMP --icmp-type echo-request -m state --state ESTABLISHED,RELATED -j ACCEPT

      #####################################################
      # Erweiterte Sicherheitsfunktionen
      # SynFlood
      $iptables -A FORWARD -p tcp --syn -m limit --limit 1/s -j ACCEPT
      # PortScan
      $iptables -A FORWARD -p tcp --tcp-flags SYN,ACK,FIN,RST RST -m limit --limit 1/s -j ACCEPT
      # Ping-of-Death
      $iptables -A FORWARD -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT

      #####################################################
      # bestehende Verbindungen akzeptieren
      $iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
      $iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

      #####################################################
      # Garbage übergeben wenn nicht erlaubt
      $iptables -A INPUT -m state --state NEW,INVALID -j garbage

      #####################################################
      # alles verbieten was bisher erlaubt war
      $iptables -A INPUT -j garbage
      $iptables -A OUTPUT -j garbage
      $iptables -A FORWARD -j garbage
      ;;
```

---

### Post by Dylan1473 on 2012-08-06
Maybe I'm misunderstanding since I don't speak the same language as your comments (German?) and didn't read through all the rules below, but it looks like at the very beginning you've set the default behaviour to drop EVERYTHING. Unless you for some reason feel the need to stop outbound traffic from all but a small specific set of ports, you don't want to do that. Blocking inbound traffic by default is a fine idea, but you should allow outbound (again unless you have some reason not to).

Anyway, my knowledge of IPTABLES is less than exceptional and it's been a while since I've configured it, but I *think* what you need to do is change this line:

```
$iptables -P OUTPUT DROP


```to this:

```

$iptables -P OUTPUT ACCEPT

```You might need to change your default forwarding rule as well, but I don't think so. Anyway, that's just my barely-informed guess, but give it a try and see what happens. Not like you can't reset it after.

---

### Post by jhmgbl on 2012-08-07
Hallo!

I need to drop outbound access because I want to restrict Access to the internet to only a few domains (whitelist).

Regards

Hans

---

### Post by Dylan1473 on 2012-08-07
I'm not certain exactly how to do this myself, but have you taken a look at [this]("http://ubuntuforums.org/showthread.php?t=1537138")? I think someone is asking a similar question to what you want there and they've received some helpful answers.

---

### Post by chadk5utc on 2012-08-10
Hello there are a couple of things. First Default policy is correct :
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP
The rules you post after this are exceptions to the rule in that they will allow the specified connection to take place. That which you have not explicitly allowed is implicitly denied. 

If I understand this you are using dynamic ip addressing via DHCP? connecting to your router wirelessly  if so try:
sudo iptables -A OUTPUT -p udp --dport 68 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 67 -j ACCEPT

---

### Post by jhmgbl on 2012-08-10
Hallo!

I am using a static ipaddress. Everything seems to work OK, but when wicd checks the connection it stops saying "connection point not found" (this is a translation from german!).

Regards 

Hans

---

### Post by jhmgbl on 2012-08-10
Hallo,

I checked the wicd logs and found out that ping was not working. After changing the icmp settings wicd was working from the beginning.

Regards

Hans

---

