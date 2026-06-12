---
title: "Cant VNC over SSH, error message not detailed"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by Slates on 2010-02-04
I have successfully connected to my ubuntu server from XP using VNC over SSH from within my internal network.

But when I try from an external network I can SSH but VNC times out.

Using netstat I see vino server listening on 5900.

Using ps -ef I see vnc and vino-server and vino.

In auth.log I see :

Feb  4 17:07:25 DellD600 sshd[8754]: error: connect_to 123.243.**.** port 5900: failed.
Feb  4 17:11:14 DellD600 sshd[8754]: error: connect_to 123.243.**.** port 5900: failed.

These entries coincide with when vnc times out, after a minute or so.

I have tried realVNC and TightVNC with similar results. 

Im connecting specifying localhost in VNC and port 5900 in and out in putty - same as I do when connecting locally. 

The error messages dont give me a lot to go on.

Can anyone suggest where else I can look, or anything else I can try, or suggestions as to what could be wrong. 

Im assuming the problem must be on the ubuntu server itself since Im getting in through SSH and hitting the logs ?

Any advice welcomed !

---

### Post by Slates on 2010-02-04
OK, Ive found the potential problem, but I dont understand why.

Once SSHd in I my ubuntu sends out a request addressed to my public IP on port 5900. My firewall blocks it.

Why would the vnc server on ububtu send out a request on port 5900 to anywhere when Im tunnelling through SSH ?

It certainly didnt get a request in on port 5900 because it isnt open. Only 22 is open for SSH (and that works because Im SSHd in noproblem).

While I Could open up port 5900 outbound on my firewall Im reluctant to do so because it defeats the whole purpose of SSH tunnelling to my mind ?

Does anyone have a comprehensive understanding of this and how it really should be !

---

### Post by Slates on 2010-02-04
Specifically my router/firewall is complaining thus :


home.gateway:firewall:info: 286531.748 Blocked Prot=6, 123.243.**.**:48002 > 192.168.1.254:5900, S Seq=-1848469644, Ack=0 -Disallowed Destination IP

So why is my ubuntu server (on an internal 192.168 address) asking to connect to 192.168.1.254 (my router) on port 5900 when Ive tunnelled through SSH on port 22 ? I just dont get it !!

---

### Post by CharlesA on 2010-02-04
Do you have something like tightvnc installed?

If you do, try this:

Forward local port 5900 to remote address of 127.0.0.1:5960

Once you connect run this: vncserver :60

See if you can connect that way.

---

### Post by Slates on 2010-02-05
I have tight vnc and realvnc. Same deal with both.

I tried your suggestions, but I get the same thing only my firewall complains about port 5960 (instead of 5900).

I just dont get why vnc is even trying to get out from my server on port 5900/5960 when its supposed to be using SSH on port 22 ?

---

### Post by CharlesA on 2010-02-05
It is supposed to be sending VNC commands over SSH. I'm not quite sure what is causing the problem.

Is this a clean install or one that has been up and running for a while?

Do you have the builtin remote client disabled?

I've found that, while I could VNC in using the built-in server, my server needed to be logged in.. which is why I went with TightVNC (until I said screw it and didn't bother installing a GUI)

Also: What happened if you try to connect to tightvnc using port 5960 and the server's local IP address?

---

### Post by Slates on 2010-02-05
OK we might be getting closer here ! 

Yes this is a clean brand new install, wiped everything else off the PC. First use of Ubuntu (can you tell !).

In fact no, I dont have the builtin remote client disabled - assuming you mean have I gone into the GUI and disallowed remote access to my PC. Because I could VNC over SSH from within my network, Id assumed all was well and it should be fine from outside, save the firewall.

Would I be right in assuing I need to disable the builtin and then somehow check vncserver is upand running and listening on the right ports ? How do I ensure that s set up correctly (althohgh I do see vncserver already listening).

If the two are completely separate programs I guess the builtin remote client is perhaps taking presenence ? In fact what executable is the remote client if its not vncserver ? (you can see Im interested as much in why and how as fixing the problem !).

---

### Post by Slates on 2010-02-05
OK, a bit of research reveals my guess isnt right. The inbuilt desktop of Ubuntu seems to come with vncserver, which is presumably why I see it running. 

So fo course I do need remote desktop enabled/accepting connections on my server. And I know its working because I can vnc over ssh on my internal network (and vnc directly come to that because the ports are all open internally.

Back to the drawing borad I guess :roll:.

---

### Post by Menthu_Rae on 2010-02-05
When I tunnel through SSH to use VNC, I do the following:

* On the "server" back home or wherever, have your VNC server running - for me this is achieved via:

```
x11vnc -usepw -forever -noxdamage -nolookup -q -repeat
```

* On the "client" out somewhere, at work or on site or something, SSH back into your "server" at home... note you usually need port 22 open on your router or have another port forwarded to 22 internally, or use port knocking, etc...

```
ssh user@server.ip.address -L 5900:localhost:5900
```

Now, on your "client", run your VNC viewer app... for me, this is

```
xvnc4viewer
```

Then I put in:

```
localhost:5900
```

And click "OK" and bam - there is my VNC session tunnelled through SSH. No need to do anything with ports 5900/etc - you only need port 22 (or port 22 forwarded) open on your router and pointing internally.

---

### Post by Slates on 2010-02-05
Thankyou for your reply ... 

This is effectively what I am doing, I believe, except I allow the GUI to start up vnc server by enabling access via remote desktop under remote desktop preferences.

This all works with vnc over ssh in my local network no problems, from which I assume I have it right. So, specifically, I start up SSH, log in. Then I start VCNviewer specifying localhost. That connects to SSH which has a tunnel set up from localhost on 5900 to the remote on 5900. All works fine in my local network.

Just to check for sanity . I have even just disallowed port 5900 in or out on the firewall on my client PC within my local network. So if either my client PC or the server attempts to use port 5900 it should get bounced by my client pc firewall.

But it doesnt. It works fine and only logs the use of port 22 as I expect.

yet when doing exactly the same thing from a remote connection my router firewall blocks a request outgoing to my public IP on port 5900. So, to be specific, I use putty to ssh, vncviewer connecting on localhost and SSH tunnelled from 5900 to my public IP on 5900. My router has port 22 forwarded to my server. SSH connects fine.

I just can fathom this out. WHy would my router firewall even see a request on 5900 ?

I am right in assuming if I can VNC over SSH specifying localhost in VNC I have this setup correctly internally ?

---

### Post by Menthu_Rae on 2010-02-06
Maybe there's some kind of bug/issue with vino's server (the inbuilt VNC client).

Disable the inbuilt VNC server and you should be sweet to use the x11vnc server.

Add the command I gave you into your "Startup Applications" folder under System > Preferences.

Make sure you set a VNC password **first** though by running the command in terminal and putting in a password when prompted. ;)

---

### Post by Slates on 2010-02-06
OK, thankyou for the advice. Im trying this now, but have some 'technical difficulties' which I should really post separately as its really a different topic. Ill come back to this when I have it working (olr not !) to report progress ! ...

thanks

---

### Post by CharlesA on 2010-02-06
Good luck. It could be that the builtin VNC server is causing conflicts or something.

---

### Post by Slates on 2010-02-07
No joy. Ive disabled the builtin desktop. Ive installed x11vnc. It works just fine on my local network. No requests on port 5900 as expected.

However externally I get the exact same thing. 

Very strange.

So Ive started a new thread ([http://ubuntuforums.org/showthread.php?p=8791025#post8791025](http://ubuntuforums.org/showthread.php?p=8791025#post8791025))because the title of this one is not really representative of what it has now become about ! 

thanks for all your help thus far. This one is hurting my brain !

---

