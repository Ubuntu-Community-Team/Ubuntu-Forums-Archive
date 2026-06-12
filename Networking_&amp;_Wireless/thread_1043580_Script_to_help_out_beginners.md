---
title: "Script to help out beginners"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by terminator14 on 2009-01-18
A few months ago, after repeatedly recommending Ubuntu to people who were fed up with Windows, and then having to try to explain to those people how to set something up over the phone when they had trouble getting something to work (like installing a video player, or flash for firefox), I had an idea of making a script that would simplify the process of introducing someone to Ubuntu. The script was never meant to be a public one, but after many hours of working on it, I thought I would at least post it for those who could find a use for it, as well as get some feedback on the commands I used. The function of the script is fairly simple:

Install:

VLC
Amarok
Wine
OpenOffice 3
unrar
flash player
java
realplayer
and the most useful of all, SSH.

[COLOR="Red"]Code has been removed by slavik, see my reply below. --slavik[/COLOR]

WARNING - Do not run this script on your main system as it probably will mess something up. This script is basically beta and should only be run on an Ubuntu Live CD or VMware for testing. You should also know EXACTLY what the script does before running it. It should only be run on Ubuntu 8.10, unless properly modified, since it replaces the sources.list file to get it's list of programs from the main server for Ubuntu 8.10 specifically.

The biggest goal of the script is for it to be able to configure SSH to use RSA authentication, and generate a text file with the user's external ip and username so they can send it to the person that gave them the script (was meant to be me but could be anyone) so that he/she may help them with any problems by securely connecting to their computer through SSH and fixing/configuring anything needed.

Plans for Improvement - 

Make script more user friendly by either making it runable by doubleclicking it (and maybe clicking run in terminal afterwords if necessary), or by writing a line that the user can paste after clicking "Alt F2"

Make script keep a log of everything and only tell the user what it is working on, not what it's doing. Running script from terminal with ">> script.log" works but it's hardly user friendly. It would be better if the script did that by itself while at the same time not having to append that to every line

It would be nicer if at the end of the script, the message boxes would be permanently on top of the program that is opened, and if the user couldn't just click ok right away, killing the program that just opened, but ok would activate in a few seconds after the program launched. This would be annoying, especially to people who know all that and just want to skip it, so either a different way has to be implemented, or the user can be asked if they want to run the tutorial.

Before installing and configuring SSH, explain to the user what it is and if they want to install it so that it is less of a backdoor. It would also be nice if the user was assured of their privacy by being able to only turn on SSHD when they want help, and leaving it off the rest of the time. That way they control when someone connects to their computer and not the client.

Make script make sure user has internet before running

Bugs - 

At the end of the script, if something like openoffice takes a while to open and the user clicks ok on the message box before it does, openoffice will probably not shut down and the next program will open, piling them up.

Also, at the end of the script, the programs that are opened are killed and not really shut down, which is bad

If there is an installer already running (updates, synaptic...) the installer would have blocked the system from installing anything else at the same time, which means the "sudo apt-get install ..." commands in the script will fail, and the commands following that which depend on those programs to have successfully been installed will fail and possibly screw up the system. If something locked out apt, the script should end and inform the user.

The AutoPort feature is supposed to scan the external ip for open ports and choose one automatically to use for SSHD. Unfortunately, despite it doing this, the first port it found on my system that was open (port 53) failed to connect. Need to find a way to scan only for ports that are open and unused. Worst case, try to connect through ssh to itself on every open port until it finds one that works.

Any feedback on this would be appreciated. 

BTW in case anyone cares, I give anyone permission to use/edit/distribute the script however they see fit, as long as it is not modified to create a backdoor to someone's system without the owner's knowledge.

---

### Post by reviver on 2009-01-21
I really like the idea of this.  I know I'll be setting up a desktop with Ubuntu soon for someone and this would be good to look into.  I'll take a look at it over the next couple of days.

---

### Post by terminator14 on 2009-01-21
If you plan to use it, please be careful. You may also want to turn off the AutoPort feature if you are using the SSH portion of the script by setting the ```
AutoPort='true'
``` to ```
AutoPort='false'
``` as this feature is not working properly yet. It seems to find a port that's open ok but that port is usually open because something is using it so the ssh connection fails. Or if you don't need the SSH, just comment that part out. And don't run the ```
echo '# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted...' > /etc/apt/sources.list

``` portion of the code unless you are specifically running it on Ubuntu 8.10.

Sorry, you probably already know all this... I'd be more than happy if my script helps someone - I'd just hate to have it break someone's system. I'll keep working on it, if I have time, to make it more interactive, user friendly, graphical, and safe. I'll post it here if I make major improvements to it.

---

### Post by dmizer on 2009-01-22
Thank you for your script, it was well though out and I am glad you find it helpful.

Would you mind adding a few warnings or advice about the security implications of installing a ssh server? Also the "without-password" option is confusing and alarming to people who may not be as familiar as you are with sshd_config.

We also try to encourage people to contribute their scripts / code to alternate locations such as launchpad or sourceforge as these may be more appropriate then the Ubuntu forums.

Thank you,
dmizer

---

### Post by slavik on 2009-01-22
I saved a copy of your code and will restore it after you answer some of my concerns.

You replace the SSH config with something that allows root logon without a password. You are also changing the default SSH port and are pointing to a site that is behind DynDNS.

As it stands, your script is a big security risk. (Running SSH on an off port doesn't help).

---

### Post by terminator14 on 2009-01-24
> **slavik said:**
> I saved a copy of your code and will restore it after you answer some of my concerns.

You replace the SSH config with something that allows root logon without a password. You are also changing the default SSH port and are pointing to a site that is behind DynDNS.

As it stands, your script is a big security risk. (Running SSH on an off port doesn't help).

I understand that my code may pose a security risk if someone manages to use it on an unsuspecting user's computer to gain access to it over the Internet, but it is in no way meant for that.

I had the sshd_config file replaced to do specifically that so that the client (the guy who is connecting to the computer through ssh) doesn't need to know the root password. Most people use the same password for their email, their banking information, and things like that, so if the user was to give up his root pass to accomplish this connection, the client would have access to more than the user's system. The way I was configuring it was so that the client could supply his own pass, as he is generating the rsa keys, and use that pass instead of asking the user what their pass is. This exposes as little private information as possible to the client, while at the same time allowing them root access, which is required to fix even the most simple problems the user could have run into.

The default SSH port is changed because of the many recommendations I read online as I was learning to use SSH that said to do so to prevent hackers from finding this ssh connection and trying to brute force it.

As for the DynDNS point you brought up - I'm not entirely sure what you mean. Do you mean the site that finds your external IP? I think I may have accidentally left that part in there without actually using it. I deleted some of the code before putting it online, including the id_rsa.pub that I was using to test the script, and another part at the bottom that had a message box popup and tell the user to send me their username and IP if they wanted me to connect to them and help them with any problems. Since users may not know what their Username is (unlikely but possible) and may not know what their external IP is (very likely), I had gedit open up in the background with the user's username and External IP so they had the info that they should send. The part of the script that contacted a webpage gathered this external IP for that purpose. I deleted it because the script was only meant to be used between people who know each other. This means that the external IP could have been gathered by other means, such as email, from the user after the client explained to the user how to find their external IP. By deleting it, I was hoping to make it harder for people to use my script as a backdoor, since then any potential hackers trying to use my script would have to write their own code to find out the user's external IP and send it to themselves all from the script. Unfortunately I guess I forgot to get rid of the main part that acquires the external IP.

If my script poses any kind of security risk, then by all means delete it, and I won't post it again.

---

### Post by slavik on 2009-02-02
if you are setting up a system for someone, create your own user account and give it sudo access. write a script with zenity that would display all the needed info. (there is whatismyip.com, too).

nmap is a powerful tool, using a different port won't hide you

---

### Post by terminator14 on 2009-02-09
> **slavik said:**
> if you are setting up a system for someone, create your own user account and give it sudo access. 

I was hoping to change the user's system as little as possible besides the actual applications installed, and the ssh - creating a new username sounds like a pretty big change for a system. Depending on the way the user logs in, the new username may show up on the login as a name which may annoy some users since they didn't create that username and it would be always there. I imagine there is a way to hide that (declare the username as a system account or something) but I'm not sure how to do that. Is there any advantage to creating a new username for this task and giving it sudo access?

> **slavik said:**
> write a script with zenity that would display all the needed info.

A while ago I came upon a script online that was written to use zenity, before which I've never heard of it. Once I saw what it could do, and found out that it was built into the standard install of Ubuntu, I've been playing around with it trying to learn how to use it to be able to make my script more user friendly.

> **slavik said:**
> (there is whatismyip.com, too).


I know of the site, and might use zenity to create a message that says something like "please visit whatismyip.com to find out your external IP address as this will be needed by anyone trying to connect to you remotely"

> **slavik said:**
> nmap is a powerful tool, using a different port won't hide you

I suppose not from an attack directly targeted at the ssh server, since all ports can be scanned quite easily, but if there is a bot running that scans random ip addresses for ssh connections, it would take it forever to find a large quantity of IPs that have ssh connections if it scans every port on every IP so I think most bots would only scan the default port and if it fails, move on to a different IP. Am I mistaken?

---

