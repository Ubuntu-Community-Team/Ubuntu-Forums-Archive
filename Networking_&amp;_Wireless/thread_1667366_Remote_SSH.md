---
title: "Remote SSH"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by Happyman7 on 2011-01-14
Hi

I have been Googling and forum-searching for a way into SSH to a computer in my home network from outside that network, at say..McDonald's.

Stuff involved:
[B]
Dell Dimension 4400[/B]

[LIST]
[*] It's in an Old computer running samba on my home/local network
[*] Has openssh-server running on it
[*] Connected to wireless router via cat5e cable,
[*] Running Ubuntu 10.04 LTS Desktop
[LIST]
[*]    It has "text" entered after "quiet splash" in it's grub.cfg file, so it boots up in text           mode
[/LIST]
 
[*] IP: 192.168.9.7
[*] [COLOR=Red]I am going to be SSHing **into** this device[/COLOR]
[/LIST]
 
**Linksy's WRT310N** running DD-WRT mini

[LIST]
[*] Connected to a (crappy) 2WIRE router that has wireless disabled so it is basically acting as a modem
[*] Here is a picture of the port forwarding setup:
[/LIST]
 [IMG]http://img143.imageshack.us/img143/5388/routerscrnsht.jpg[/IMG]

**iPod Touch** 4G 32GB running iOS4

[LIST]
[*] Jailbroken
[*] Has Mobile Terminal 472
[*] I have made certain I can SSH from it
[*] [COLOR=Red]I am going to be SSHing **from** this device[/COLOR]
[/LIST]
 
Would I have to enter a few extra commands in order to do this?
[I]----
I have searched and did find a few threads/posts about, but they weren't very clear.
----

One more question that isn't in any way correlated with the original one:[/I]
What does "|" do in the command line?

---

### Post by Mr_Mischif on 2011-01-14
I'll take a crack at this:

From what I understand you haven't tried to connect yet, the command to connect from your iTouch should be:

```
ssh username@home.wan.ip.address
```

accept your home server's RSA key, enter your password and away you go.

As for your second question "|" is the "pipe" command, it takes the output of one program and uses it as the input of another program. For example, try the command

```
ls -l
```

in a folder with a lot of objects, then try

```
 ls -l | less
```

in the same folder to get what I'm talking about.

---

### Post by Happyman7 on 2011-01-14
> **Mr_Mischif said:**
> I'll take a crack at this:

From what I understand you haven't tried to connect yet, the command to connect from your iTouch should be:

```
ssh [COLOR=DarkRed]username[/COLOR]@[COLOR=Blue]home.wan.ip.address[/COLOR]
```accept your home server's RSA key, enter your password and away you go.

I have tried to connect, but ended with failure.

So the [COLOR=DarkRed]username[/COLOR] would be the same username that I use when I log in via SSH from within the network, if I understand correctly.

What I don't understand is the [COLOR=Blue]home.wan.ip.address[/COLOR] thing, would that be the IP number I get from here: [http://www.whatismyip.com/ ]("http://www.whatismyip.com/")?

If so, would the command I enter be this?:
```
ssh regularusername@IPfromthatwebsiteIjustsuggested
```-----------

And for the pipe command, by *program*, you mean *command*, right?

Thanks for the fast reply :)

---

### Post by papibe on 2011-01-14
Could you confirm the config?

Internet -> 2Wire -> Linksys -> Dell


Is that it?

---

### Post by Happyman7 on 2011-01-15
> **papibe said:**
> Could you confirm the config?

Internet -> 2Wire -> Linksys -> Dell


Is that it?

Yes.

---

### Post by papibe on 2011-01-15
Then, it is important that the configuration of the 2 router are "coordinated".

In order for a connection to the port 22 be established between the Internet and your Dell, it needs to find its path through both routers. Something like:

2Wire: 22 from internet forward to Linksys IP.
Linksys: 22 from outside forward to your Dell (as is).

Onother simple solution would be to set the 2Wire's firewall settings to DMZ (all open), so the security and port forwarding would be done exclusively in the LinkSys.

I hope it helps.

---

