---
title: "how to see a local site of one system on other system ?"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by chinmaya_n on 2009-08-17
hi

I would like to show my present working drupal site to my friends.
Previously i used to show it like "[COLOR="Blue"]http://myip/sitename[/COLOR]" but i recently changed my ISP (Internet Service Provider). From then i could nt do the previous thing, b'se if i use 'ifconfig' it is showing local IP address.
When i used the site [http://whatismyipaddress.com/](http://whatismyipaddress.com/) to find my IP, it is shownig some other !
 When i tried the new one like "[COLOR="Blue"]http://newip/[/COLOR]" it is throwning an error saying "currently unavailable!"

Can anyone solve my problem?? plz help me :(

---

### Post by jamest09 on 2009-08-17
Have a look into dyndns.com

---

### Post by aledujke on 2009-08-17
I do not think it will solve his problem >.>

What he needs is to set up dmz? demilitarized zone... or alternatively to open up the ports on his router and forward them to his workstation. I guess you have a router since ifconf shows you a local ip a private one? Something like 192.168.0.1? Right?

I would suggest you to forward port 8080 to your machine and set up apache to listen on that port...

Then you could send your friends something like: [http://ipfromwhatsmyip:8080/site_dir/](http://ipfromwhatsmyip:8080/site_dir/)

cheers!

---

### Post by chinmaya_n on 2009-08-18
> **aledujke said:**
> 
I would suggest you to forward port 8080 to your machine and set up apache to listen on that port...

Then you could send your friends something like: [http://ipfromwhatsmyip:8080/site_dir/](http://ipfromwhatsmyip:8080/site_dir/)

cheers!

I dont know what do u mean by that, How to forward port 8080 to my machine and set up apache there. (I alredy 've apache on my machine)

Which ip address i should use, ip shown by ifconfig or by [http://whatismyipaddress.com/](http://whatismyipaddress.com/)

Thanx

---

### Post by Stoneface on 2009-08-18
You should use your external ip address, not your internal. So use [http://www.whatismyip.com/](http://www.whatismyip.com/) to determine your external ip.

---

### Post by aledujke on 2009-08-18
go here:[http://portforward.com/](http://portforward.com/)

Find your router model, and use the guide from above site to forward port 8080 or 80 (standard apache port) to your machine, ip of your machine. That you mentioned you see with ifconfig command.

Now If you have forwarded port 8080 and not port 80 go to apache's ports.conf file and find where to change the default port that apache is listening on. It should be pretty straight forward.

If you installed apache server the ubuntu way (via apt-get) then the ports.conf location should be /etc/apache2/ports.conf - this file is included by apache2.conf that is in the same dir. so if you did not installed apache the ubuntu way the variable might be in apache2.conf or httpd.conf

NameVirtualHost *:80
Listen 80

should be I think:

NameVirtualHost *:8080
Listen 8080

restart apache...

now go to [http://www.whatismyip.com/](http://www.whatismyip.com/) or some other similar site to obtain your wan (public) ip and try the link:
[http://your_public_ip:8080/yoursitedir/](http://your_public_ip:8080/yoursitedir/) or just [http://your_public_ip/yoursitedir/](http://your_public_ip/yoursitedir/) if you used the default http port.

Hope it works.

---

