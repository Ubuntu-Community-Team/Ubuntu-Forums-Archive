---
title: "would someone talk me through an ftp install?"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by Lakeside5 on 2010-09-23
Ok I'm being wimpy here, but just about ready to give up  lol  I've read and tried a lot of things but I still can't install components into Joomla because I don't seem to have set up  ftp properly despite following tutorials. I tried using fireFTP, gFTP and vsftpd (which I installed using the ubuntu terminal but not sure if it's actually installed).  I'm using ubuntu 10.04 desktop with wamp installed, and had it hosting the joomla site I(it worked, I could see it at it's domain url).  I tried putting in what I thought was the right username and password (the username and password I use to log onto my computer, the ubuntu OS).  for 'host' I just put 'localhost' or ftp.localhost. And in the joomla configuration file I entered that same info, and for ftp path I put  /var/www (the joomla site's root).  But I STILL got the 'ftp failted to connect to server' when tryiing to install components. And I can't get the  ftp client to work either so I can change folder permissions, although I've read other posts that say one SHOULDN'T change the permissions, it is safer to leave them at 755, not change to  777, so I am further confused. I really want to be able to do this so I can help to non-profit groups here to have a nice website. I look forward to taking this step by step, thanks!

---

### Post by CharlesA on 2010-09-23
Why not just use sftp to transfer files instead of ftp?

It would be easier to configure and secure.

Also: It kinda helps to break up your post into segments instead of leaving it as a large block of text.

---

### Post by Lakeside5 on 2010-09-24
lol, yes, sorry I'm sure the huge post put most people off :)  Thanks for responding, I hope this is a start. I have fireFTP and enabled gFTP (synaptics package) and installed (I think)  'vsftp' from the terminal.  Should I uninstall all these and start again installing sftp? Maybe that would be a start? 
I see that ssh and ssh client are already enable in my Lucid Lynx synaptics package manager, so i guess I already have them. Can you please tell me what my next step would be? I would greatly appreciate your advice. Thank you.

---

### Post by pmlxuser on 2010-09-24
you can use all of them, its a matter of taste, as for me i like using gftp. simple but does the job...

---

### Post by Lakeside5 on 2010-09-24
Oh, well I tried using all of them and couldn't get any to work. I think I will try the sftp, based on what I have been reading so far, if someone could just please tell me what to do next :) thanks. (Although,  I do really like the fireFTP, just not sure if it isas secure as sftp? )

---

### Post by pricetech on 2010-09-24
sftp uses SSH, which is secure.  FTP is inherently insecure regardless of which FTP server you choose.

Frankly, the fact that you have more than one FTP server installed could be an issue since all of them would want to listen on the same port.

Try removing all but one if you still want FTP or remove them all and use SSH instead.

If you need a windows client, I like WinSCP myself.

---

### Post by Lakeside5 on 2010-09-24
Well, I know I don't want a windows client.  So I am going to uninstall gFTP, vsFTP and fireFTP, I'm just wondering how to uninstall them.  Also I want to use ssh (which seems to be installed on ubuntu by default. So how would I use the ssh? How to get it started, and which client?  Also I'm still wondering about the host/username/password fields.  With sftp would I put 'ftpd://localhost' or 'sftp.localhost' or what?
*edit* I would like an opinion: I am going to do everything it says on this tutorial here: (for a password required ssh). Does that sound like a plan? Also, I am going to uninstall the other ftp clients, so I guess I would do that in the syaptics package manager or...? thanks  *edit*   ooops here is the site: [http://www.linux.com/archive/feed/62254](http://www.linux.com/archive/feed/62254)

---

### Post by Lakeside5 on 2010-09-26
solved, in a way.  I do have ssh installed now (sftp) and am using gFTP, and it seems to work to the point where I can log onto gFTP, enter username/password, have 'localhost'  for host, and transfer files between folders of my website (joomla, it he www root) and even change permissions.  BUT, I still cannot 'connect to the server' when in the Joomla backend installer so I can't install components etc. I must have something wrong in the configuration.php file for Joomla, but what? Please can someone help? Thanks you very much.

---

### Post by Lakeside5 on 2010-09-27
Anyone? :(

---

