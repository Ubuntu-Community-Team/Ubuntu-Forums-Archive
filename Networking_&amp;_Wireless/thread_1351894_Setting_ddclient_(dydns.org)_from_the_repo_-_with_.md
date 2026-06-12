---
title: "Setting ddclient (dydns.org) from the repo - with multi network cards (How)"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by nomnex on 2009-12-11
I have posted my question in the wrong topic I am afraid:

see: [http://ubuntuforums.org/showthread.php?t=1351873](http://ubuntuforums.org/showthread.php?t=1351873) (in absolute beginner talk)

Mood: could you move the thread to Networking & Wireless or merge it with this one if someone answer?

---

### Post by puppywhacker on 2009-12-11
In normal situations where you only have one internet connection, you would only need the internet connected interface to update your dns record. In the special case you do have two interfaces edit the configuration textfile /etc/ddclient.conf yourself. I think () you can use 2 stanza's, so first ppp0 and then eth0. If that doesn't work report back and we'll create two instances of ddclient.

As for which port to forward, that would not be needed, since dyndns is not actively contacting you, it only passively responds to your requests. If you want to run a webserver you'll need to forward port 80. but I if you'll need to forward ports to your server it's behind a nat ... then it will be very tricky for ddclient to figure out that your ip-address has changed

```

protocol=dyndns2
use=if, if=ppp0
server=members.dyndns.org
login=mylogin
password='mypass'
external.domain.com

protocol=dyndns2
use=if, if=eth0
server=members.dyndns.org
login=mylogin
password='mypass'
internal.domain.com
```

---

### Post by nomnex on 2009-12-11
thanks for helping puppywaker,

It's the first time I am setting a dynamical ip client. the network topic on Linux is quite a primer. Can you elaborate the following:

> In normal situations where you only have one internet connection, you would only need the internet connected interface to update your dns recordThere is one notebook usually wired to the NAT router and sometimes wireless (bathroom ;-)). it is OR and not AND. Does the sentence in the quotes means that, either eth0, either wanl0 in the config window is fine, since the script will update the current live connection by default?

Furthermore, could you explain me following. especially this

> ppp0 and then eth0eth0 is my ethernet card (the wired one). What is ppp0? It relates to my questions below, when I re-run the ddnclient config using the command

```
dpk-reconfigure ddnclient
```> **See: print-screen 1**

What is run ddnclient on PPP connect? I have selected <YES>. Please advice/explain.

**See: print screen 2**

Run ddnclient as daemon. I have selected <YES>. I assume this is like a service runing in the background? Please advice if wrong setting.

**Next window setting (no print screen)**

The default refresh interval time was 300 s. I have left it untouched.PS: I am not in front of a Linux box at the moment, I will copy my /etc/ddclient.conf and past it in the message tomorrow.


EDIT: I had missed this one

> but I if you'll need to forward ports to your server it's behind a nat ... then it will be very tricky for ddclient to figure out that your ip-address has changedCorrect, my notebook acts as a 'webserver' (big word) when I am online (html/ftp). Port 80/22 are already open on the router, thanks. I don't get the sentence in the quote. Is it relevant with my configuration? What does means 'if you'll need to forward ports to your server it's behind a nat..'? sorry about it.

---

### Post by puppywhacker on 2009-12-11
aha, so you are behind a nat, so the public ip-address will be on the router all the time. That means that if the public ip-address changes you will have to do an update to dyn-dns. My adsl-modem has a feature that will update dyndns when the address changes (the feature uses ddclient on the adsl-modem).

Now the problem is that ddclient will always have to poll to an external webserver to find out 'whatismyip' at the moment and if that has changed it will do the update to dyn-dns

A DNS update is not instantly, there are TTL timers that will have to expire before the change is propagate through all the DNS servers on the internet. So if you change "position" the dns may not have updated in time.

Also your eth0 and wlan0 need to have the same ip-address which is kind of confusing for routing from the modem to your laptop, and visa versa.

(I first thought your second interface was ppp0)

I think there are a few if's and but's here that I don't think this will work reliably.

As for the practical solution, in your situation you don't need to update the status of eth0 and wlan0 to dyn-dns, because the configuration is about which interface changes address. That is because of your NAT not applicable, so either interface will work. what you need is the "web" approach, where your ddclient.conf would look like this

```
daemon=300
pid=/var/run/ddclient.pid
ssl=yes
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
login=your-username
password=your-password
protocol=dyndns2
server=members.dyndns.org
your-hostname
```

---

### Post by nomnex on 2009-12-13
here is my config file (default - wizard settings)

```
# Configuration file for ddclient generated by debconf
#
# /etc/ddclient.conf

pid=/var/run/ddclient.pid
protocol=dyndns2
use=if, if=eth0
server=members.dyndns.org
login='mylogin'
password='mypassword'
'myhostname.dyndns.og'
```here is a print screen I have taken of my dyndns.org account page (see: attached print screen). It seems to be working since - awkwardly - it does not display my public IP anymore, but the LAN IP (behind the NAT) of the machine. Is this normal?

I am not sure if I am processing correctly all your information, but I used to have the same type of web server on Windows (behind a NAT/Ethernet & Wireless connections). the dyndns dynamic IP client software was updating correctly my IP changes at TTL (Time To Live) every 60 s. (Default dynamic DNS value)

My NAT router is a not a newer model. I don't have this function,  I guess? I have a Buffalo router and its web interface setting is in Japanese (there's a bunch of Kanji I can't read). Could you do me a favor and send a print screen of the page you make the dydns settings. It could give me a hint where to search on my side.

Either when I connect through the Ethernet card, either through the Wireless card, my LAN IP does not change. I should be fine on this side.

Sorry I don't understand the following (bold in the quotes):

> As for the practical solution, in your situation you don't need to update the status of eth0 and wlan0 to dyn-dns, **because the configuration is about which interface changes address. That is because of your NAT not applicable, so either interface will work. what you need is the "web" approach, where your ddclient.conf would look like this**It would help if you could translate the codes below in plain English

```
use=if, if=eth0
```vs.```
use=web, web=checkip.dyndns.com/, web-skip='IP Address'

```My understanding of a dynamic IP client software was to simply broadcast my current IP address to the dyndns.com server at a regular interval.

I still don't understand the difference between PPP0 or eth0. The best definition I have found is here: [http://www.faqs.org/docs/Linux-HOWTO/PPP-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/PPP-HOWTO.html). Is PPP an interface for dial-up modems or peer-to-peer connection?

---

### Post by puppywhacker on 2009-12-14
Hi,

I am feeding you a lot of information because I don't know your exact goal, so I'm giving you plenty to google on, not everything I say is relevant, but I can only figure that out based on your feedback. For instance eth0 is a wired ethernet interface, ppp0 is a dailup interface, wlan0 is a wireless ethernet. You don't have an ppp0, I mistook your first message to be ppp0 instead of wlan0, they are just possible interfaces, one you have the otherone I imagined...

What I have learned from your setup is that your internal ip-address remains the same over eth0 or wlan0 ... and the updates TTL within a minute.

What you do now is update your internal private ip-address to the public DNS. that private address is not routable from the internet. Addresses starting with 192.168. are to be used for internal networks only.

So what you need to do is update your external public address. For this ddclient config needs to use=web since your PC doesn't know it's public address. ddclient will then go to a website, which will report back the public address. Which is then sent to dyndns.

replace
```
use=if, if=eth0

```by
```
use=web, web=checkip.dyndns.com/, web-skip='IP Address'

```

---

### Post by nomnex on 2009-12-18
Alright, so first I want to thank you.

Then

> What you do now is update your internal private ip-address to the public DNS. that private address is not routable from the internet. Addresses starting with 192.168. are to be used for internal networks only.Makes sens. I have changed the line in the config file

```
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
```When I log-in on DynDNS.com, the host service tab displays the correct external IP address and updates regularly.

Now, if I was to move outside for a while (e.g. at my friend's place, using my friend's router IP address) would my server still be reachable? I guess the answer's yes looking at the line above. Thanks to confirm.

---

### Post by jeanathon on 2011-08-15
> **puppywhacker said:**
> In normal situations where you only have one internet connection, you would only need the internet connected interface to update your dns record. In the special case you do have two interfaces edit the configuration textfile /etc/ddclient.conf yourself. I think () you can use 2 stanza's, so first ppp0 and then eth0. If that doesn't work report back and we'll create two instances of ddclient.


```

protocol=dyndns2
use=if, if=ppp0
server=members.dyndns.org
login=mylogin
password='mypass'
external.domain.com

protocol=dyndns2
use=if, if=eth0
server=members.dyndns.org
login=mylogin
password='mypass'
internal.domain.com
```

Due to a local south eastern dsl carrier (and their incompetence) that I will not name I have set up a multi isp box.  ppp0 is with them and static and eth2 is a dynamic cable ip.  I would like all domain related stuff (email, www) to go through ppp0, but when it goes down switch the domain name over to the cable modem.  Would this two stanza set up work if ppp0 just wasn't there or is it going cause ddclient to quit?  I only want the ip to change if/when the adsl line goes down, and perhaps go back to the dsl if/when it comes back up.

---

