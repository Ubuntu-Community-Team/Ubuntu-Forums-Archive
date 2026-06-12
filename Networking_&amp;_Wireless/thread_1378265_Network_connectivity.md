---
title: "Network connectivity"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by nishant.singh28 on 2010-01-11
I am a college student. I use my LAN to access the Internet. Now our connection is such that we have to keep a browser window running in the background. It is a sort of login page. It keeps refreshing itself after 200 seconds and the connection is through. But sometimes, the connection acts funny so the Keepalive Window disappears and the connection breaks. It is not a problem when I am in my room but when I'm off to class or asleep at night, I can't monitor it. I need the connection to work as I use torrents frequently and the download stops and I lose a lot of time. Is there a way to keep checking the connection and reconnect automatically?
PS-Browser in use: Google Chrome. TO reconnect, I simply have to press home button in the browser(my homepage is Google) as trying to navigate to any page outside LAN when the Authentication Keepalive Window is not open brings up the Login screen. I have the username and password saved. I just have to press continue to connect.

---

### Post by nishant.singh28 on 2010-01-11
First image is of the Login screen, second of the Keepalive Window

---

### Post by changingstate on 2010-01-11
My initial attack on this would be to simply pass the refresh url to wget and call it from the crontab every three mins ( 180 seconds ).

Something along the lines of :

*/3 * * * * wget <the url the refreshing script passes to the webserver>

Info on crontab editing here : [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

If you need to work out the refresh url, either look at the source code for the web page, or use wireshark to observe the traffic your machine is requesting.

[B]I ALSO RECOMMEND THAT YOU CHECK DOING THIS DOESN'T BREACH THE USAGE POLICIES FOR YOUR NETWORK. 
[/B]

---

### Post by nishant.singh28 on 2010-01-11
> **changingstate said:**
> My initial attack on this would be to simply pass the refresh url to wget and call it from the crontab every three mins ( 180 seconds ).

Something along the lines of :

*/3 * * * * wget <the url the refreshing script passes to the webserver>

Info on crontab editing here : [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

If you need to work out the refresh url, either look at the source code for the web page, or use wireshark to observe the traffic your machine is requesting.

[B]I ALSO RECOMMEND THAT YOU CHECK DOING THIS DOESN'T BREACH THE USAGE POLICIES FOR YOUR NETWORK. 
[/B]
Does not work:(.No probs about Violation, the college does not mind anything as far as net connections go or we wouldn't be able to get 10+MBPS download speeds from the Internet. And the trouble is, okay, if the link breaks for a couple of minutes it is no problem but if the connection is out for more, I get logged out automatically and have to log back in. How do I do that?

---

### Post by tripolitan on 2010-01-11
Chainstate's solution should keep the connection alive. Is wget installed? post the script that refreshes the connection...

---

### Post by changingstate on 2010-01-11
As far as it not working, I can only suggest you try looking the results of running a wget manually and see what the response is. That should shed further light on the situation. 

If you want to start automating login, you'll need to script it. You'll want to grab a page and check to see if you're logged in ( something along the lines of wget, dump results to file, cat and grep the file should work, off the top of my head ) then send a string with the correct post arguments to the web server if required.

---

### Post by nishant.singh28 on 2010-01-11
> **changingstate said:**
> As far as it not working, I can only suggest you try looking the results of running a wget manually and see what the response is. That should shed further light on the situation. 

If you want to start automating login, you'll need to script it. You'll want to grab a page and check to see if you're logged in ( something along the lines of wget, dump results to file, cat and grep the file should work, off the top of my head ) then send a string with the correct post arguments to the web server if required.
```
nishant@Nishant-Studio:~$ wget https://172.31.1.251:1003/keepalive?0c0200060a0f6cbd
--2010-01-11 22:08:20--  https://172.31.1.251:1003/keepalive?0c0200060a0f6cbd
Connecting to 172.31.1.251:1003... connected.
ERROR: cannot verify 172.31.1.251's certificate, issued by `/CN=FG3K6A3407600677/O=Fortinet Ltd.':
  Self-signed certificate encountered.
ERROR: certificate common name `FG3K6A3407600677' doesn't match requested host name `172.31.1.251'.
To connect to 172.31.1.251 insecurely, use `--no-check-certificate'.
Unable to establish SSL connection.
```SSL Error always shows up in Chrome too.
```
nishant@Nishant-Studio:~$ wget https://172.31.1.251:1003/keepalive?0c0200060a0f6cbd --no-check-certificate
--2010-01-11 22:11:06--  https://172.31.1.251:1003/keepalive?0c0200060a0f6cbd
Connecting to 172.31.1.251:1003... connected.
WARNING: cannot verify 172.31.1.251's certificate, issued by `/CN=FG3K6A3407600677/O=Fortinet Ltd.':
  Self-signed certificate encountered.
WARNING: certificate common name `FG3K6A3407600677' doesn't match requested host name `172.31.1.251'.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.

```
One more thing. I CAN and I HAVE copied the link above from one browser and pasted it in another to keep the window running and it works.

---

### Post by nishant.singh28 on 2010-01-11
And I am not an expert. I am an average user with virtually no knowledge about scripting. So please treat me gently :D.

---

### Post by changingstate on 2010-01-11
Okay, Nishant. Try wget again, but like this :

wget --no-check-certificate <insert refresh url here>

wget and chrome are complaining about the certificate the IT dept are using not being one they paid for and not being generated for that server. The command option I've added should get wget to ignore it, according too : [http://www.gnu.org/software/wget/manual/html_node/HTTPS-_0028SSL_002fTLS_0029-Options.html](http://www.gnu.org/software/wget/manual/html_node/HTTPS-_0028SSL_002fTLS_0029-Options.html)

> And I am not an expert. I am an average user with virtually no knowledge about scripting. So please treat me gently :grin:.     It's in your own best interests to learn, if you write the script you'll understand how to fix, it if the IT dept change anything and it breaks. There's a great tutorial on scripting here : [http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

---

### Post by nishant.singh28 on 2010-01-11
> **changingstate said:**
> 
It's in your own best interests to learn, if you write the script you'll understand how to fix, it if the IT dept change anything and it breaks. There's a great tutorial on scripting here : [http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)
I'll learn it. give me some breathing space folks. I've switched to Ubuntu after around 13-14 years of Windows usage. One month is too little a time to learn everything about an OS. So, help me out please :D. Don't worry, Ill learn it within a few months.
Thanks anyway.

---

### Post by nishant.singh28 on 2010-01-12
Bump!!!

---

