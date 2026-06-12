---
title: "small business web site"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by remsy on 2006-07-14
I have a small business and would like to setup ubuntu as a web server. Besides registering the domain name, what other steps are necessary to achieve this goal?

---

### Post by OpsVentus on 2006-07-14
-Getting your DNS sorted out.
-Writing a website.
-Install web server.

edit:
-Tell people about it

---

### Post by remsy on 2006-07-14
I see. So, what does it involve to get DNS sorted out? does it require installing a gateway?

thanks

---

### Post by T700 on 2006-07-14
Is there a particular reason you want to host this yourself?  Setting up a server is quite a bit of work and unless done correctly and constantly kept updated, it is an open door to hackers.

With hosting solutions starting at just a few dollars a month (US prices in July 06), I would not want to run my own server, outside of some really pressing need.

Paul

---

### Post by az on 2006-07-14
It involves getting your ISP to handle your domain name.  

What kind of website do you want?

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
See the web applications section.

Also:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by remsy on 2006-07-14
I also would like to open a session remotely using ssh tunneling or something for development/administration purposes. So basically, I want to host my own web server + rlogin (via putty, etc.). That's why I mentioned the gateway.

thanks

---

### Post by OpsVentus on 2006-07-14
For ssh you just install an ssh-server. For the web-server you can use apache.
Then you need to point the adres:[www.yourcooldomain.whatever](www.yourcooldomain.whatever) to the ip-adres of your computer.
I've got my domain at godaddy.com, there you can easly do this.

After this your website will be visible on the net and your ssh availible.
But watch out! Getting your security figured out is the hard part.

No gateway needed, but a fixed internet-ip-adres on your server is handy. Other wise you will have to update your dns every time your ip-adres changes. And this will take up to 2 days.
Unless you got something like no-ip.org setup.

---

### Post by remsy on 2006-07-14
Thanks a lot OpsVentus. I posted another thread on how to make the ssh server accessible from outside my LAN.

Remsy

---

### Post by tturrisi on 2006-07-14
I do NOT recommend running a business site on a home computer UNLESS you have a business class internet service from your isp.  The reasons are many:
1. It is a violation of the isp's TOS to run a home server www server if have residential service.
2. It requires much much more than just installing server software.
3. Even if config the services properly & securly, you will still need to use an online service like DynamicDNS to point www users toward your domain name.
4. The trouble with DynamicDNS type services is that search engines will ignore those sites because they cannot be properly indexed.  usually, your site is embedded in a hidden frameset in order to get the domain name to appear in the browser address bar instead of the ip address in the address bar.
5. Web hosting is very cheap unless want ssh.  Hosting with ssh will cost much more.  Unless you are storing confidential data or doing ecommerce then you don't need ssh anyway, you can get by with ftp.
6. back to the isp issues:  most US isps filter port 80 and you will be forced to use a generic tcp port for the www server.
7. It will take you at minimum 12-24 work hrs to properly setup & config a www server with other essential services like mysql, php, openssh, etc.  I could buy web hosting three fold in that time by actually working 12 hrs & earning between 600 & 1200 bucks!

Cheap reliable hosting:
[http://www.ipowerweb.com/](http://www.ipowerweb.com/)
[https://www.godaddy.com/gdshop/default.asp](https://www.godaddy.com/gdshop/default.asp)
[http://www.hostway.com/](http://www.hostway.com/)

---

### Post by OpsVentus on 2006-07-15
Yes there are a lot of reasons why you don't want to host your self. To name another(important) one: the speed will be much much lower on your home connection then on a good hoster. But if you want there are more options.
If you want to host yourself, you can very easy. But if you want quality and want to depend on it you will see hosting it yourself is not the way to go.

For making the ssh server accessible from outside your LAN, you just need to forward the port to your server in your router. To make it more easy you can setup a DNS-name to point to your internet-ip-adres. Then you can type a dns-name in stead of a ip-address.

To finish:
You can do everyting yourself, it's easy. But you WILL find it's more expensive, takes more time and is less reliable.

Good luck,
Bart.

---

### Post by GuitarHero on 2006-07-15
most isp's dont allow you to run web servers.

---

### Post by tturrisi on 2006-07-16
other tips:
If hosting your own server you will be subject to more port scans and potential attacks from would be criminals.  There are common known ports that will get looked for often; ports 80, 22, 3000 to name a few.  Port 80 is www, 22 is telnet or ssh & 3000 is default phomyadmin port.  On my home servers I use port 8090 for www, 3022 for ssh & keep phpmyadmin closed until I need to use it & then open it via the router.

---

