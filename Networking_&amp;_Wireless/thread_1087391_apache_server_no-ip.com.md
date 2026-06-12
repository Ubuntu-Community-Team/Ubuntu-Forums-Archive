---
title: "apache server no-ip.com"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by TCSnyder on 2009-03-05
I have apache running and working but i was wanting to be able to access it from the outside world, aka the web,my ip blocks port 80 so i went to /etc/apache2/ports.conf or whatever and changed it to listen to port 84.

it still doesnt work.

i set up my router to port forward 84 to 84 at my internal ip address.

still doesnt work.

i disabled my firewall and it still doesnt work.

is there anything i missed? 

the page is tylor.no-ip.org:84 is what i am trying to get

---

### Post by Huufarted on 2009-03-05
Have you restarted apache?

```
sudo /etc/init.d/apache2 restart
```

then try it

---

### Post by TCSnyder on 2009-03-05
yea i did that

---

### Post by Huufarted on 2009-03-05
type this:  netstat -an | grep 84

anything listed?

---

### Post by TCSnyder on 2009-03-05
```
netstat -an | grep 84
tcp        0      0 0.0.0.0:84              0.0.0.0:*               LISTEN     
unix  2      [ ACC ]     STREAM     LISTENING     89109    /tmp/orbit-tylor/linc-3b8b-0-6505ea8487c5a
unix  2      [ ACC ]     STREAM     LISTENING     16784    /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     88455    /tmp/orbit-tylor/linc-3b65-0-10468abe9b334
unix  2      [ ACC ]     STREAM     LISTENING     88595    /tmp/orbit-tylor/linc-3b6c-0-e6383a937b84
unix  3      [ ]         STREAM     CONNECTED     163848   @/tmp/dbus-zwqvOmgumo
unix  3      [ ]         STREAM     CONNECTED     163847   
unix  3      [ ]         STREAM     CONNECTED     96284    /tmp/orbit-tylor/linc-3aba-0-4fa7bd6e82ce1
unix  3      [ ]         STREAM     CONNECTED     89144    /tmp/orbit-tylor/linc-3b8b-0-6505ea8487c5a
unix  3      [ ]         STREAM     CONNECTED     89076    /tmp/orbit-tylor/linc-3b6c-0-e6383a937b84
unix  3      [ ]         STREAM     CONNECTED     89061    /tmp/orbit-tylor/linc-3b6c-0-e6383a937b84
unix  3      [ ]         STREAM     CONNECTED     88896    /tmp/orbit-tylor/linc-3b6c-0-e6383a937b84
unix  3      [ ]         STREAM     CONNECTED     88849    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     88848    
unix  3      [ ]         STREAM     CONNECTED     88584    @/tmp/dbus-IyF0jbJsfp
unix  3      [ ]         STREAM     CONNECTED     88466    @/tmp/dbus-IyF0jbJsfp
unix  3      [ ]         STREAM     CONNECTED     88465    
unix  3      [ ]         STREAM     CONNECTED     88464    @/tmp/dbus-IyF0jbJsfp
unix  3      [ ]         STREAM     CONNECTED     88463    
unix  3      [ ]         STREAM     CONNECTED     88453    /tmp/orbit-tylor/linc-3aba-0-4fa7bd6e82ce1
unix  3      [ ]         STREAM     CONNECTED     88452    
unix  3      [ ]         STREAM     CONNECTED     88448    @/dbus-vfs-daemon/socket-eylZUoLR
unix  3      [ ]         STREAM     CONNECTED     88447    
unix  3      [ ]         STREAM     CONNECTED     88449    @/dbus-vfs-daemon/socket-gniFch1I
unix  3      [ ]         STREAM     CONNECTED     88446    
unix  3      [ ]         STREAM     CONNECTED     88440    @/tmp/dbus-IyF0jbJsfp
unix  3      [ ]         STREAM     CONNECTED     88439    
unix  3      [ ]         STREAM     CONNECTED     88458    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     88457    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     86884    
unix  3      [ ]         STREAM     CONNECTED     86849    /tmp/orbit-tylor/linc-3aba-0-4fa7bd6e82ce1
unix  3      [ ]         STREAM     CONNECTED     86848    
unix  3      [ ]         STREAM     CONNECTED     86844    @/tmp/dbus-IyF0jbJsfp
unix  3      [ ]         STREAM     CONNECTED     86843    
unix  3      [ ]         STREAM     CONNECTED     86842    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     86841    
unix  3      [ ]         STREAM     CONNECTED     86384    /tmp/orbit-tylor/linc-3aba-0-4fa7bd6e82ce1
unix  3      [ ]         STREAM     CONNECTED     86084    @/tmp/dbus-IyF0jbJsfp
unix  2      [ ]         DGRAM                    84540    
unix  3      [ ]         STREAM     CONNECTED     84251    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     84250    

```

none are port 84 though they are just ***84** and others

---

### Post by Huufarted on 2009-03-05
ah, but you're wrong!

```
tcp        0      0 0.0.0.0:84              0.0.0.0:*               LISTEN     

```

That's the server listening on port 84.  So it IS listening!  The problem is either your ISP or your router.

---

### Post by TCSnyder on 2009-03-05
here is a screenshot of my router settings, is there anything else i have to do

---

### Post by matt79 on 2009-03-05
I would set your server to port 80 and have it redirected over another port by no-ip. 
How I had mine was no-ip would take the user connecting to my site, and redirect them over port 8080. I then had my router take port 8080 and redirect it to port 80 on the local side. However, you do it, make sure that your server has a static ip address from your router, and make sure that it is 192.168.1.100. That way you do not have to worry about having your  ip address change if you were to restart the server or something.
If you want to see what your ip address is type "ifconfig".

---

### Post by Huufarted on 2009-03-05
Everything looks good to go there assuming your server is on .100 for an IP address.  If you still can't access it, I'd put the blame on your ISP.

(For the record, I have the same router)

---

### Post by TCSnyder on 2009-03-05
well i saw somewhere where someone said their isp blocked all ports under 1024. i moved mine with no luck, i have no-ip sending data through port 3030
and no avail

---

### Post by TCSnyder on 2009-03-05
i am using this site
[http://canyouseeme.org/]("http://canyouseeme.org/")

to check if my port is open, is there another way to do this?

---

### Post by Huufarted on 2009-03-05
TCSnyder, if you don't mind me asking, what's your ISP?  Perhaps they block all unsolicited network traffic?  A google search would probably reveal that.

---

### Post by Huufarted on 2009-03-05
> **TCSnyder said:**
> i am using this site
[http://canyouseeme.org/]("http://canyouseeme.org/")

to check if my port is open, is there another way to do this?

I like that!  Bookmarked.

---

### Post by TCSnyder on 2009-03-05
i have comcast

---

### Post by Huufarted on 2009-03-05
> **TCSnyder said:**
> i am using this site
[http://canyouseeme.org/]("http://canyouseeme.org/")

to check if my port is open, is there another way to do this?

What's your IP?  Your firewall might not enjoy this, but we can throw an anal probe at it with 'nmap' and map anything that is open.  Firewalls hate it sometimes for obvious reasons, but that's a risk I'm willing to take!

---

### Post by Huufarted on 2009-03-05
> **TCSnyder said:**
> i have comcast

I use Comcast as well (Northern Utah here) and nothing is blocked for my connection.

---

### Post by TCSnyder on 2009-03-05
my ip is 76.123.212.143

---

### Post by TCSnyder on 2009-03-05
if i portscan localhost it tells me port 84 is open.
port 84 is where i am going to leave my www port

---

### Post by TCSnyder on 2009-03-05
should i be able to pull up my webpage from the internal network?
i read somewhere people were having problems with it.

will someone try to go to [tylor.no-ip.org]("tylor.no-ip.org")

---

### Post by TCSnyder on 2009-03-05
**bump**

---

### Post by Huufarted on 2009-03-05
nmap isn't even seeing that IP address.  Doesn't respond to pings, forced it to scan all ports 1-1024 and it didn't find a single open port.

nmap -p 1-1024 76.123.212.143

---

### Post by TCSnyder on 2009-03-05
i use 
```
nslookup tylor.no-ip.com
```

and it points to my computer. i just dont know whats wrong

---

### Post by TCSnyder on 2009-03-05
> **Huufarted said:**
> nmap isn't even seeing that IP address.  Doesn't respond to pings, forced it to scan all ports 1-1024 and it didn't find a single open port.

nmap -p 1-1024 76.123.212.143

guess i don't have to worry about hackers

---

### Post by TCSnyder on 2009-03-05
i went and had a portscan by ShieldsUP 

attached is a picture of the results.

all of my ports are green "Steath"

and in their words
> If your system is unprotected, without any personal firewall or NAT router, any ports showing as stealth are being blocked somewhere between your computer and the public Internet. This is probably being done by your ISP. Internet traffic directed to your computer at the stealth ports will be dropped before reaching your machine.

---

### Post by TCSnyder on 2009-03-05
ok i fixed it, i didnt realize my comcast cable modem had 2 ports, so it had it's own port forwarding. but can i forward from my cable modem, to my router, to my pc?

---

### Post by Huufarted on 2009-03-05
TCSnyder, my recommendation is to bypass the router functionality entirely from your cable modem and just use your router.  But assuming you know how to forward the ports in the cable modem, there's no reason you can't set it up to forward the port through both devices.

---

### Post by TCSnyder on 2009-03-05
thanks, it is up and running now

---

