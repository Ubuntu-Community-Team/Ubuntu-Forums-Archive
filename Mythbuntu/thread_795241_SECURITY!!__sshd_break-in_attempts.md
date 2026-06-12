---
title: "SECURITY!!  sshd break-in attempts"
date: 2008-05-15
forum: Mythbuntu
---

### Post by karlec on 2008-05-15
Has anyone noticed attempts to break into their machines in recent days?
While checking the logs yesterday, I noticed quite a few attempts at breaking in using ssh.  I had attempted to use port forwarding in order to access my machine from the internet through mythweb, and when I got home yesterday, the break-in attempts were all over the logs.  It did not seem like they were able to break in, but I immediately disabled port forwarding in my router/firewall and it seemed to have stopped.

I still was not able to access through mythweb though.  The question is how do I set-up access through mythweb through the internet whithout being subjected to these attacks or at least knowing that I am 'fairly' secured.

Thanks

---

### Post by laga on 2008-05-15
It happens quite often that people are scanning for open ssh ports. There's been a recent vulnerability in OpenSSH/OpenSSL. Check this announcement: [http://ubuntuforums.org/announcement.php?f=301](http://ubuntuforums.org/announcement.php?f=301)

*edit:* To answer your original question: those port scans are usually harmless if you've got good passwords (and no vulnerable ssh keys for key-based authentication). You can use tools like "fail2ban" to ban people from your box after they've used the wrong password for 5 times or so (configurable). Port-knocking might also be a good option, but you'll have to carry the port knock client with you.

---

### Post by az on 2008-05-15
> **laga said:**
> It happens quite often that people are scanning for open ssh ports. There's been a recent vulnerability in OpenSSH/OpenSSL. Check this announcement: [http://ubuntuforums.org/announcement.php?f=301](http://ubuntuforums.org/announcement.php?f=301)

*edit:* To answer your original question: those port scans are usually harmless if you've got good passwords (and no vulnerable ssh keys for key-based authentication). You can use tools like "fail2ban" to ban people from your box after they've used the wrong password for 5 times or so (configurable). Port-knocking might also be a good option, but you'll have to carry the port knock client with you.

I use denyhost:
[http://packages.ubuntu.com/hardy/denyhosts](http://packages.ubuntu.com/hardy/denyhosts)
DenyHosts is a program that automatically blocks ssh brute-force attacks by adding entries to /etc/hosts.deny. It will also inform Linux administrators about offending hosts, attacked users and suspicious logins.

You just install it and forget it.

---

### Post by davilla on 2008-05-15
I use dd-wrt as the firewall/router and it supports a VPN service. My access to mythweb (and everything else behind the firewall is through a VPN connection. 

In the past, I had an ssh port open but I closed that down and went with a VPN connection. Safe secure and I don't have to worry about bots and script-kiddies continually trying to get in through ssh. The rapid knockers that are doing dictionary lookup are easy to block, it's the slow knockers (one try per day) that I was worried about, very hard to detect and block.

---

### Post by karlec on 2008-05-15
> **davilla said:**
> I use dd-wrt as the firewall/router and it supports a VPN service. My access to mythweb (and everything else behind the firewall is through a VPN connection. 

In the past, I had an ssh port open but I closed that down and went with a VPN connection. Safe secure and I don't have to worry about bots and script-kiddies continually trying to get in through ssh. The rapid knockers that are doing dictionary lookup are easy to block, it's the slow knockers (one try per day) that I was worried about, very hard to detect and block.

My Linksys also provides a firewall/router. The problem that I see is that you will need to always use a machine that has a VPN client on it and I don't necessarily carry my laptop with me everyday and everywhere that I go.
Is there a 'complete' step by step howto on how to access mythbuntu using mythweb with a Linksys router?

---

### Post by eldragon on 2008-05-15
to keep your security to the max, and still be able to access your computer from away, do the following:

only allow ssh, switching to an alternate port is a good idea too.
have a strong password.
install fail2ban which will disable logins (for 10 mins) for ips which have too many failed logins (over 3). this will prevent bruteforcing.
connect to other services via ssh tunneling.

so, if you want to connect to port 80 in your computer with a sshd running,

connect to sshd with
```

ssh -L 80:localhost:80 user@server

```
and then access from the computer you are using, to localhost:80 and it will sent to the server at the port 80.

the transmission is encrypted too, so no worries for snoopers.

thats what i do, i dont even set passwords for vnc, which makes it convenient for management within the LAN.

if you only use a laptop of your own, you can set automated logins for ssh with public/private key pairs. which will make everything more automatic :D

cheers

---

### Post by Salla101 on 2008-05-15
I use fail2ban to prevent hackers.
I have it set to ban IP's on the 3rd failed attempt, it generates an email to me and the IP host provider with an email of the IP that was banned and what they were trying to access..FTP, SSH, HTTP, etc.

sudo apt-get install fail2ban

You will need to configure some of the files but its pretty simple.

---

### Post by ScorpKing on 2008-05-15
new security updates for ssh has been released. just install then. you might also find honeyd usefull.

---

### Post by karlec on 2008-05-24
Not to be paranoid but I have noticed several root sessions opened in the auth.log at times when I was not around.  I am the only one to use my mythbuntu box so far.
I have seen the following in the logs, is this something that I should be concerned about?
```
root : TTY=unknown ; PWD=/ ; USER=Me ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
```

---

### Post by qaelith_2112 on 2008-06-02
> **karlec said:**
> Not to be paranoid but I have noticed several root sessions opened in the auth.log at times when I was not around.  I am the only one to use my mythbuntu box so far.
I have seen the following in the logs, is this something that I should be concerned about?
```
root : TTY=unknown ; PWD=/ ; USER=Me ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
```


I'm using Ubuntu 8.04 Server (not Mythbuntu), and this is happening to me as well.  Lately I've been getting this particular log entry every day.  I've searched and found lots of other examples of this, but no one is asking about it as such.  It always shows up in search results as part of a log where people are asking about something else in their log.  

I haven't installed X on my system, let alone Gnome.  I wouldn't expect to be seeing this.  Strange, though, /usr/bin/gconftool does exist.  I'm not sure why, or how it got there.

---

### Post by superm1 on 2008-06-02
> **karlec said:**
> Not to be paranoid but I have noticed several root sessions opened in the auth.log at times when I was not around.  I am the only one to use my mythbuntu box so far.
I have seen the following in the logs, is this something that I should be concerned about?
```
root : TTY=unknown ; PWD=/ ; USER=Me ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
```
*Please* make sure you install the latest security updates.

---

### Post by karlec on 2008-06-02
I have installed every update that has been made available so far.  Is there anything else that I need to do?  Does this mean that my machine has been breached?

---

### Post by superm1 on 2008-06-02
> **karlec said:**
> I have installed every update that has been made available so far.  Is there anything else that I need to do?  Does this mean that my machine has been breached?
If you have all the updates from hardy-security, i would recommend changing all passwords and removing .ssh from root and all user's home directories (they can be rebuilt).

Sounds like someone might have made their way in at some point.

---

### Post by karlec on 2008-06-03
> **superm1 said:**
> *Please* make sure you install the latest security updates.

Anything in particular that needs to be installed besides the normal updates that were available?

---

### Post by foobunt on 2008-06-13
Every Day? Same Time? Cronjob!

```

me@mymachine~# grep gconf /etc/cron.daily/apt

# set the proxy based on the admin users gconf settings
if [ -n "$admin_user" ] && [ -x /usr/bin/sudo ] && [ -z "$http_proxy" ] && [ -x /usr/bin/gconftool ]; then
        use=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/use_http_proxy)
        host=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/host)
        port=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/port)


```

Not found on Gutsy but on Hardy.

Regards :)

---

### Post by qaelith_2112 on 2008-06-13
Foobunt:

Thank you for pointing me to the source of this!  I had a lapse of thought and didn't even go to the obvious cron.daily as a likely source for this recurring activity.  

I had also mentioned that being on a console-only SERVER installation of Hardy, I had no idea how I came to have any of the Gnome components installed.  Weeeeeelllll......... that's no longer an unknown either.  Checking my logbook (I keep track of what I do to the server), I see that I foolishly followed selective parts of the "Hardy Heron Perfect Server Setup Guide" in this particular installation.  One of the recommendations was to install vim-full, which on a console-only environment is a big mistake.  That carries gvim with it, which as a dependency installs pretty much the whole X plus gnome baggage that I don't want on my server.  In a moment of laziness, I just agreed to the whole list of dependencies (and there was a screen full of them) and didn't read through what it wanted to install.  

That, and a few other bits of really bad advice, have left me cold on the Perfect Server Setup Guide.  I'll probably reinstall my server one weekend rather than try to manually remove all of the extra crap that I inadvertently installed along with vim-full.  I don't want a GUI on my server.

I wasn't really thinking it likely that my system had been compromised, as this predictable pattern seemed anything but an incursion, but nonetheless it was bothering me to see it in the log and not know the origin.  Thank you again for uncovering that for me (and for the other guy).

---

### Post by djamu on 2008-07-19
my 5 cents

I use fail2ban on iptables which is preferable over denyhosts because it works on the (iptables) firewall level,  and by doing so offloads your CPU in case of a (d)dos .

but:
**[SIZE="4"]hardy fail2ban_0.8.2-2_all.deb is broken ! [/SIZE] **

there's a bug in the hardy version that prevents it from starting on reboot 

Due to /var/run being mounted as tmpfs, after a reboot, the /var/run/fail2ban is no longer present and prevents fail2ban ( hardy ) from starting. This is a known issue but the lazy devs just ignore it & keep it in the repos .... 
:twisted: ( that version shouldn't even be there )

in other words after a reboot your system is available for brute force without the owner noticing ...


**solution > use fail2ban_0.8.2-3_all.deb > entrepid or debian version **

get it here > [http://packages.ubuntu.com/intrepid/all/fail2ban/download]("http://packages.ubuntu.com/intrepid/all/fail2ban/download") 

desktop install > just double klik the *.deb file

CLI install > ```
sudo dpkg -i fail2ban_0.8.2-3_all.deb
```



another thing that one should do is limit the users that may connect thru an ssh session 
```
sudo vim /etc/ssh/sshd_config
```

and add a line at the end

```
AllowUsers yourusername anotheruser moreusers
```

replace yourusername with ... well guess you get what i mean ... space separate all usernames


additionally you could change the 
```
PermitRootLogin yes
```
to
```
PermitRootLogin no
```
but if you excluded root in the AllowUsers that is not necessary 

you can change the default port nr here too


if you are really paranoid you can use a portknocking daemon.
this prevents 0-day exploits ( newly discovered weaknesses against unpatched services ) like the recently discovered ssh one
DO NOT USE THIS AS A SINGLE DEFENSE.

more info here > [http://www.portknocking.org/]("http://www.portknocking.org/") 
wiki here > [http://en.wikipedia.org/wiki/Port_knocking]("http://en.wikipedia.org/wiki/Port_knocking")

fail2ban qualifies itself as a good candidate for a portknocking daemon ( opening a port & route on a predetermined port sequence )
personally i'd rather not use one of those but instead use **fwknop** which is a single packet variant that doesn't knock ports but uses a crafted ICMP packet ( a normal PING packet with with encrypted payload ) 
Using icmp packets has the advantage of being capable of carrying a large cyphered key, it's likely to be unnoticed by packet sniffers ( it looks like a normal ping ) & it will not be noticed by any IDS as it only requires 1 packet.

you can find fwknop here >  [http://cipherdyne.org/fwknop/]("http://cipherdyne.org/fwknop/")

:guitar:

have fun..

---

### Post by YaroMan86 on 2008-07-19
I just changed the port for my sshd. I trust denyhosts implicitly.

---

### Post by nickrout on 2008-07-21
All these suggestions of good passwords are fine, but you are better to turn password authentication off altogether and rely on key based authentication (and yes it can be used from windows via putty and its cousins.)

---

### Post by djamu on 2008-07-22
> **nickrout said:**
> .....but you are better to turn password authentication off altogether and rely on key based authentication.... 

Not necessarily, as it depends on the amount & type of users.
a key is as good as the place where you put it. 
And relying on a single line of defense for ex. ssh is a not so smart thing to do ( prove of this is the recently found 0-day exploit )

On the other hand passwords are vulnerable to keyloggers running on an infected windoz computer > you just replay the passw in cli on another computer ....

It's generally accepted that static Iptable rules are a good means to preselect incoming service requests. ( whether it be passwords or keys ), but if your users travel around ( like I do ) this wont work.. Adding dynamically associated iptable rules is a final solution to key / password based authorization.

There's a lot of controversy around portknocking which can do exactly this... Most people against this added layer of security ignore it as being an added layer but think of it as a replacement for key / passw which of course it is not ... it just add a means to enable a route to your to be authenticated service. It also protects you from password replays as you can pre-initiate authentication to the desired service without having to touch a keyboard. If used with a single encrypted ICMP packet -implemented either as OTP / WPA ( OTP = One Time Pads ) replay attacks from packet sniffers are rendered useless too...


:popcorn:

---

### Post by zdude on 2008-07-22
I've setup ssh to use a different port and also key-auth with different keys/pass-paraphase for each user. This allows mobility and is pretty secure. When using key-auth only you can't even use a login with no key. I check the auth logs daily and I've yet to see anyone even find the door much less knock on it. This works really well for me (so far).

---

### Post by newlinux on 2008-07-22
I've done the security by obscurity (ssh on a different port and closing all unused ports) and I use denyhosts with a few changes to the default settings to make it more strict. when I set up denyhosts I didn't know about fail2ban. But since denyhosts and changing my ports has thwarted the breakin attempts I used to have I feel it is okay for me... Just a little work for a lot more added security...

---

