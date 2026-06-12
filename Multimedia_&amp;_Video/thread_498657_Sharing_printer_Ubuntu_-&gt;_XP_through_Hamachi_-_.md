---
title: "Sharing printer Ubuntu -&gt; XP through Hamachi - Cannot access printer url from XP comp"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by motin on 2007-07-11
Mission: Share a printer (fully working locally) from Ubuntu to an XP machine through Hamachi

It should be performed like this (used [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP) as starting point):

[LIST=1]
[*]Allow connections from IP addresses 5.*.*.* (Hamachi subnet) in /etc/cups/cupsd.conf
[*]Restart Cups
[*]Make sure the local CUPS printer url works
[*]Move oneself to chair in front of Windows box
[*]Give the Ubuntu computer a friendly hostname using a HOSTS entry with the Hamachi ip-address of the Ubuntu computer
[*]Make sure you can ping your Ubuntu computer using the friendly hostname
[*]Make sure that the ubuntu computer printer url is accessible
[*]Add printer as a network printer using that url
[/LIST]

Thing is, I did almost all, but can't continue because I cannot follow through on point no 7!

So, [http://127.0.0.1:631/printers/PSC-2210](http://127.0.0.1:631/printers/PSC-2210) works on the local computer, but [http://ubuntu-computer:631/printers/PSC-2210](http://ubuntu-computer:631/printers/PSC-2210) does not work at all (no connection to server) from the Windows box. (Tried in Firefox)

Current CUPS permissions for /:
```
<Location />
#  Order allow,deny
#  Allow localhost
#  Allow @LOCAL
  Order Deny,Allow
  Deny From All
  Allow From 127.0.0.1
#  Allow From 5.* # <-- Didn't work
#  Allow From 5.*.*.* # <-- Didn't work
  Allow From All # <-- Didn't work
</Location>

```

Please advice me what to do next! I'd really like to now what's wrong here...

---

### Post by motin on 2007-09-05
2 month bump... No-one?

I guess I should begin with 
<Location />
  Order Allow,Deny
  Allow From All
</Location>

But since it says no connection to server it doesn't even seem to connect to the cups interface. What steps can I take to debug this?

---

### Post by yota on 2007-09-05
Have you said to cups to listen to the 5.x.x.x interface?

Check it this way:
```

yota@linbook:~$ netstat -anltp |grep 631
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     -                   
yota@linbook:~$ grep Listen /etc/cups/cupsd.conf  
Listen localhost:631
Listen /var/run/cups/cups.sock

```
in my case (the default) cups is listening only on localhost, if you want to make listen on a network interface add to cupsd.conf
```

Listen 5.x.x.x:631

```
where 5.x.x.x has to be the exact address of your card.

Hope this helps!

---

### Post by motin on 2007-09-06
Thanks! That did the trick for step 7!

Actually I put Listen 5.*:631 as there are several hamachi clients that need to connect. 

Problem now is step 8. Even though I can browse the printer url perfectly fine using a browser on the windows client, it refuses to accept my printer url when I try to add it as a network printer. On the screen where one can either browse, enter address to a network computer or enter the url to the printer I try to enter it in the third field but Windows complains about it being invalid or cannot connect. It is all in Swedish so I can't give the correct error message I am afraid. 

I also tried adding the printer to a class in CUPS and adding the class instead to no avail. It didn't help to suffix "/.printer" to the printer url neither. 

Someone suggested that IIS had to be installed - is this true? Because then I guess Windows XP Home cannot add a cups printer by IPP. Do I have to configure Samba sharing instead?

Someone has some light to shred on the situation?

---

### Post by motin on 2007-10-21
Bump - Anyone?

---

### Post by motin on 2007-10-21
After upgrading to Gutsy, one does not have to edit the cups.conf file manually. Just launch your Printer settings application and in the general settings there should be two options: 1. Share printers, 2. Allow printing from the internet. 

With that set I could now add the printer to an XP Pro box at least. Haven't retried with the XP Home box.

---

