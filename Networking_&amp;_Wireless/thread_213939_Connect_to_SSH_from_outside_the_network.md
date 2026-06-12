---
title: "Connect to SSH from outside the network"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by MJRehrig on 2006-07-12
Hello, I am trying to figure out how I could ssh into my home computer so that I could back up my files from college.

I think this is right, but correct me if I am wrong...first forward or enable (it is called the virtual server on my router) the ports for ssh from the router to my computer.  Then I would have the server set up to allow for ssh login and scp and everything. Then on my computer that I have at college I would create a script and put an entry for it in cron.

The part that I was really unsure about was the part about opening those ports to my computer.  From my college computer would the syntax for ssh be something like this...

ssh <my.home.ip.address>:mike@homecomputer ./backup.sh
or 
scp -r /home/directory <my.home.ip.address>:mike@homecomputer

Would I even need the mike@homecomputer part, or would it be good enough to just have my IP address because that would be the only computer which ports are being opened to.

Sorry if any of this didn't make sense.

Thanks for any help, Ubuntu is great!

---

### Post by mogelhead on 2006-07-12
The setup you mentioned seems correct to mee; forward ports from your router to your computer and enable ssh logins (maybe ssh is on by default?).

The commands however need to be changed a little.
> **MJRehrig said:**
> 
ssh <my.home.ip.address>:mike@homecomputer ./backup.sh
or 
scp -r /home/directory <my.home.ip.address>:mike@homecomputer


The syntax is user@hostname, where hostname also can be an ip address. (See the man page for ssh)

ssh [email]mike@<my.home.ip.addr[/email]ess> ./backup.sh
or 
scp -r /home/directory [email]mike@<my.home.ip.addr[/email]ess>:

Note that you need a colon after the hostname when using the scp command.

What do you intend to do with the backup.sh script?

---

### Post by MJRehrig on 2006-08-12
I did not get to try this out, but I hope I will get time this week.  I was just wondering if having an HTTP Server on the same computer, running on port 80 would affect the SSH protocol (which works on port 22, correct?)

I wasn't really thinking when I wrote the backup.sh part.  Instead of that I guess I would just put an entry on my computer that I have at college in cron to scp my home folder to my home computer.

Thanks for your help and I will reply when I has tryed this method.

---

### Post by mogelhead on 2006-08-14
No, running an HTTP server on the same computer does not effect SSH.

Yes, SSH runs on port 22 default.

Setting up a cron job at your computer at the college to do your backups sounds like a good idea.

---

### Post by harisund on 2006-08-14
Let me get the scenarion right. 

You have a computer at college, which has all your data (and running linux, perhaps?). Then you have a computer at home, for which the IP address is say, 10.11.12.13

First and foremost make sure the SSH server is running on your home computer. In your home computer, execute 'ssh localhost' and see if you are able to log back into your own computer. If so, great. 

Next, figure out what IP address your home computer has (it will be different from 10.11.12.13). Use 'ifconfig' to figure this out. 

Then in your router, do a port forward of private 22, public 22 and enter your machine's IP address as the virtual server. Remember, the router has 2 IP addresses. One 10.11.12.13 that the external world sees, and one from your local home network. 

The only thing is, you will need to make sure the port forwarding always points to your desktop computer properly. If your computer reboots and acquires a different IP, the port forwarding won't work naturally since it will be forwarding 22 to a IP that won't exist. The work around of course is to create a static port.

That done, go to your school and see if you are able to access your home machine by 'ssh user@10.11.12.13'. This should take you to port 22 of the router, which in turn forwards it to port 22 of our server box. All should go fine. 

Once you have established SSH connectivity, it's time to get your backup script to work. Personally, I would strongly advise you to use rsync instead of ssh, since rsync is not only faster, it is also more intelligent and geared towards making backups. I rsync my laptop to both my home server box, and my school account. 

Anyway, I doubt 'ssh home_user@10.11.12.13 ./script' would work, since that would mean you are actually running the 'script' file on the home computer. I doubt if that is what you want. Instead what you must be doing is invoke the ssh command from within your script itself.

---

