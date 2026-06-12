---
title: "setting up vsftpd help!!"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by whos2know on 2009-02-24
Hi,

I'm trying to setup vsftpd and I've read you are able to set it up right out of the box and it would work. It is behind a router so I port forwarded port 20.  To test it, I went over to my friends house and installed Filezilla and typed my IP address, anonymous, and port 20 and it was unable to connect.  What am I doing wrong.  All help is welcomed.... thank you very much!!

-=Bobby=-

---

### Post by Reiger on 2009-02-24
Out of the box VSFTPD will be rather restrictive about what it does. It will for instance only allow anonymous FTP. (ftp@hostname-or-ip)

Consider spending an evening reading about and configuring /etc/vsftpd.conf.

---

### Post by lensman3 on 2009-02-24
If you have selinux running you need to run as root:

setsebool -P ftp_home_dir 1

This can take up to a few minutes to run.  Just today I had to setup vsftpd and this is what make it all work.  I added a new userid and password. Then had to run the above command.  Transferred 200 meg after wards.

I would suggest to try using sftp which is the ssh version of ftp.  Lots of windows versions with drag-and-drop windows.  This works very well too.

---

### Post by whos2know on 2009-02-26
lensman3,

I took your advice and tried using sftp.  I am really sure that I have everything setup correctly.  Seemed really easy to setup.  On my router I opened port 22 and also open my firewall port 22.  I download FileZilla to test it out on my side by entering in my ip address.  Put my User name from my box in and password... and connected just fine... went over to my neighbors house to connect and also used FilleZilla and did the same thing and it timeout when trying to connect....I then tried to ping my IP Address  from his side and it would not ping...I don't understand why... what do I do?

Bobby

---

### Post by jonobr on 2009-02-26
Just curious ,
When you say IP addresses,
What IP addresses are you using to connect?

---

### Post by whos2know on 2009-02-26
The IP Address from my ISP services.

---

### Post by whos2know on 2009-02-27
Bump

---

### Post by whos2know on 2009-02-28
hi,

This is the info I have found out so far.  After hours and hours of researching and late night frustrations on the web I don't know what to do and don't have a answer. :\

My ip is 24.144.xxx.xxx. I went to first neighbors house that I wanted to ftp with and his ip is 24.101.xxx.xxx.  My second neighbors is 24.144.xxx.xxx.  I am able to ping my second neighbor but I am unable to ping my first neighbor.  We all have the same internet provider, Armstrong Cable Zoom Internet.  What is going on?  Why can I not ping neighbor one so I can ftp to him?  And if this is not going to work, what alternatives do I have now?  I am using Ubuntu of course and he is using Vista.  I would like to stick to the ftp route but if this is going to be out of the question....what can I do? Any help would be great!! Thank you very much!! :)

-=Bobby=-

---

### Post by jonobr on 2009-03-02
The reason why ping may be working to one and not the other is that pings may be blocked at your 2nd friends house.

Pings are used to discover devices and can be seen as a security hole and are blocked by some devices and not other.

Given you have the same providor and all things being equal, its not your providor doing this.

Heres the only thing you can really do.

If you run wireshark on one machine, if you capture packets on the right interface, you should see packets going out to the 2nd machine, there may be some indication where things are getting blocked.

On the remote machine you should be able to see (or not) pings and ftp getting through.


FTP is easier to trace as you can see the packets, unlike something secure which is all tunnelled

---

### Post by whos2know on 2009-03-07
Thank you Jonobr.  I will try this this weekend.  Sorry about the late reply.. I'll let you know what I find out!!

-Bobby

---

### Post by whos2know on 2009-03-10
Jonobr,

I got the info from WireShark while I tried to connect with filezilla and was unsuccessful.  I saved the info and brought it over to my house in looked it over.  I'm not really sure what I'm looking for when I'm looking the data over and not understand it.  Could you help me understand what I should be looking for and not looking for? Or maybe should I just upload the section of the info where it starts here with the parts of mine and his IP Xed out??   thank you for all the help!!

-=Bobby=-

---

### Post by jonobr on 2009-03-10
Hello

Im not sure how I can look at this without you sending the information

I think if you want to send to me privately you can do so by going to my user name on the left hand side and select  "send private message".
I could have a look to see whats going on...

---

### Post by whos2know on 2009-04-03
Jonobr,

Thanks for your help.... I really think it's my services.... my other neighbors as well cannot connect either..and they have just changed my ip so I don't have a static IP on my cable modem so this isn't going to work out it looks like... Thank you very much though... if you have any other ideas I could do instead would be great...

-=Bobby=-

---

