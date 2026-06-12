---
title: "dialup connection problem- doesn't surf"
date: 2005-03-15
forum: Networking &amp; Wireless
---

### Post by scooby on 2005-03-15
Hi, I'm a newbie here so bear with me-
I'm trying to set up a ppp connection. I've muddled thru sudo pppconfig for awhile and seem to be almost there. I have the modem (ttyS0), and the correct init string in advanced advanced options. Other than that, I've entered the phone number, username, password, set the authentication to PAP, dynamic IP address. So now, when I type pon (or click on the modem light) it dials, and says it connects (and it does tie up the phone line). But Firefox can't browse, I can't ping any name (ie [www.google.com)](www.google.com)), etc. I've sent off an email to the isp support to find if it's something specific to their ISP; is there something else to check on my end in the advanced options? thanx for any help here

---

### Post by az on 2005-03-15
"I have the modem (ttyS0), and the correct init string in advanced advanced options. Other than that, I've entered the phone number, username, password, set the authentication to PAP, dynamic IP address"

Usually, at is all you need as an init string is ATZ.  Less is more.

Do

sudo tail -f /var/log/messages

in  a console before you do pon.  Post the output.  Also, you selected dynamic ip address?  Or did you enter nameservers by hand?  (just checking to be sure about what you meant...)

---

### Post by scooby on 2005-03-15
I couldn't get the modem to work with ATZ as the init string (the friend who gave me the modem also sent me a floppy with the string "AT&F&C1&D2"). 

Correct, I selected "dynamic IP address"- using the post on how to use sudo pppconfig as a reference. 

I just attempted 
sudo tail -f /var/log/messages
but was told "invalid option; try tail --help for more info". I read through the info, but as stated, I'm not very familiar with the options. Couldn't determine which one; verbose maybe?

I did get a response back from the ISP:
Unfortunately, we aren’t really able to tech support a Linux box as it is just so rare that any of customers use one.

 which was really helpful (not)

---

### Post by alastair on 2005-03-15
See :

man tail 

There is a "-f" option - means keep "tailing" the file as it grows.

Anyway - look at /var/log/syslog after a connection - you should see details of the PPP session - log in, connect etc.

If you can't ping by NAME i.e.

ping [www.google.com](www.google.com)

But CAN by IP address i.e.

ping 66.102.11.99

Then this is a DNS server problem.

---

### Post by scooby on 2005-03-15
Ok, this may help a lot- I apparently was able to use synaptic to get to the online repositories (I selected the 1st listed http:""  and installed mozilla browser). On a hunch, I typed in the only numeric address I knew, which was my brother's web site. It loaded (using Firefox). I still can't get the browser to browse using name addresses "www.google.com" or off any links. 

"If you can't ping by NAME i.e.

ping [www.google.com](www.google.com)

But CAN by IP address i.e.

ping 66.102.11.99

Then this is a DNS server problem."

I just logged back on, didn't yet expore "man tail" etc (just now reading that :oops: ); but apparently the above quote indicates a DNS server problem. What then are my options? thanx for patience

---

### Post by alastair on 2005-03-15
You either know DNS servers to use (from your ISP say) or get them auto configured (sent to you) via DHCP dynamically on connection.

The relevant file is :

/etc/resolv.conf

This lists DNS nameservers used.

On PPP connection, you will sometimes see DNS servers listed by the other computer - see the log file /var/log/syslog. This might be something configurable using pppconfig.

---

### Post by scooby on 2005-03-15
boy, do I feel sheepish.........
I had spent a lot of time previously fighting the modem (until I discovered the init string issue); had deleted and created quite a few times. Once I got the modem to work I flew thru the process and overlooked the static/dynamic IP issue (I was hitting 'enter", not "spacebar")-  duh! Maybe I need to start taking ritalin....
Anyway I went and set it correctly and am now typing from my internet-ready linux box. Thank you all very much for the help guys!

---

