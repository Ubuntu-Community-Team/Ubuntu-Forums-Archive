---
title: "vnc setup"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by 987a654 on 2010-08-07
I am trying to setup the most efficient way to remotely administer an ubuntu system.

So far I was successful in setting up ssh. I have the server running and made sure it only uses keys to authenticate and changed the default port.
I can connect to the ssh-server. 

This system is behind nat and bots trying to break-in when I forwarded the port. I used the AllowUsers option, which helped in knocking back these rouge connections. I was not comfortable leaving a port open all the time, so I set up logmein Hamachi VPN and closed the ports that were open on NAT. 

Now I use Hamachi and am very impressed. I use VNC in VPN. But Vino is slow, I tested x11vnc and it was slightly faster. I also tried to set up freenx but nxsetup file was missing. some one posted that file in the forums and suggested copying to the system but I was not sure if  I want to download  a script from the forum and use it. So for the time being, I thought I will just concentrate on X11vnc until freenx is fixed.

I would like to get the following things working, any help would be appreciated:

[LIST]
[*]I would like to create a separate desktop on the server and use it to access remotely. This way we will not have to fight over the cursor (sounds funny but very frustrating). From what I understand x11vnc has this function inbuilt (uses vncserver). I cannot get it to work!!

[*]when using ssh, at the remote machine's command prompt, if I type "evince xyz.pdf", it does not launch the "xyz.pdf". what am I doing wrong?

[*]When using VNC, how can I change between different users on the remote machines? Right now I can only use VNC in one account that I first setup. When I try to change to another user, vnc client goes blank.

[*]How can I get as much control of the remote system as possible? Right now  I need someone to switch on the remote system and login to their account before I can VNC.

[*]Can I use ekiga inside VPN, I use skype right now and it's sometimes terrible with dropouts. I looked around and someone suggested using ekiga as it works very well over lan. How do set up ekiga so that I have a direct connection with the remote system? Is there any client that just takes the IP address and creates a connection? Mumble seems to be the popular choice, it's most suited to LANparties, I just need a connection between two systems. 
[/LIST]

I am trying to set this up to help users with hardly any computer knowledge to use the system without any issues.

Thankyou.
Yudi

---

### Post by YesWeCan on 2010-08-07
Hi. Don't use Vino. Use tightvncserver on the server.
sudo apt-get install tightvncserver
You do not need to be logged on at the server console.
You can export as many, independent desktops as you like.
Each desktop can be for a different user.
Each desktop has its own consecutive port number starting with 5901

I use tightvncserver on my Ubuntu 10.04 64-bit server. I have a point-to-point OpenvPN tunnel between my Ubuntu client and the server. I use Vinagre on my client to view the remote desktop.

---

### Post by 987a654 on 2010-08-08
Yeswecan -

I already have x11vnc setup on the remote machine, and can connect to it. From what I understand tightvnc and x11vnc use quite a lot of similar components. It took me a long time to get things working, I would like to stick to x11vnc. 

since I can ssh to the remote machine, I am thinking I will setup a .x11vncrc file with the following options, then I can just type x11vnc in the ssh terminal. 

Could someone check if I am using the proper options.


wait 50        
-localhost   	
rfbauth  /home/user/.vnc/passwd
-autoport 5901 		

-timeout 600 		
-allow x.xx.xx.xx  	
-listdpy		
-usepw  		
-solid 			
-logfile file		
-v			
#-bg			
-skip_lockkeys  	
-remote command 	
display :1

---

### Post by krunge on 2010-08-08
The -listdpy makes no sense I think, x11vnc just lists them and then exits:  [http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-listdpy](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-listdpy)

Your '-remote command' similarly makes no sense.

Also, is there a reason why you want to increase the -wait time to 50ms?  Most people would find that too laggy for typing, etc.

---

### Post by 987a654 on 2010-08-10
at last the right person to talk to.

Thanks for the reply.

I got most of these commands after reading the faq and command line options on your website. It took me long time. I pretty much picked all the commands that made sense to me. and the wait 50 from the faq 8.


I am using the following options in the .x11vncrc 

localhost
autoport 5901
timeout 600
usepw
solid
v
display :0


using x11vnc slightly improved performance, reduced lag to manageable level.

I am using remmina vnc client and is there anything I can do to speed up things. 

-ncache n option - do I add this to the .x11vncrc file?

Now to secure this connection I am using -localhost option and ssh using something like the following command

sitting-here> ssh -t -v -C-p 35000 -L5900:localhost:5901 far-away.east 'x11vnc'

everything seems to be working fine, except -solid, it worked couple of times but does not work anymore.

one of the comments after  I connect is as follows

The VNC desktop is:      localhost:1
PORT=5901

Why is it localhost:1 I thought it should be localhost:0?

I would like x11vnc to listen on port 5901 as I want to leave 5900 for vino as a back up. Should I use 
rfbport 5901
-N option (I guess it would be -1, but my X display is 0 right!)
or is the autoport 5901 enough?
There is another option rfbport str??

there's one more thing I would like to get working as well.

I would like to create an additional desktop and connect to it so that we will not have to struggle for the cursor. the following link has some instructions, it's at the end of the page but there is no xstartup file in ~/.vnc/.

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)

---

### Post by krunge on 2010-08-11
> **987a654 said:**
> 
I am using the following options in the .x11vncrc 

localhost
autoport 5901
timeout 600
usepw
solid
v
display :0

Looks reasonable.
> 
I am using remmina vnc client and is there anything I can do to speed up things. 

-ncache n option - do I add this to the .x11vncrc file?

Yes.  I suggest "-ncache 10" for the value of n.

Note that depending on the viewer the -ncache mode may look very confusing to you.  More info here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)[/INDENT]

I have never used remmina.

> 
Now to secure this connection I am using -localhost option and ssh using something like the following command

sitting-here> ssh -t -v -C-p 35000 -L5900:localhost:5901 far-away.east 'x11vnc'

That looks pretty good (except -C-p looks like a typo)

x11vnc listens on 5901 on the remote side, and you point your viewer at localhost:5900 on the local side. 
> 
everything seems to be working fine, except -solid, it worked couple of times but does not work anymore.

The -solid option is highly dependent on the desktop being used. For example it has been broken for years on KDE4 and KDE doesn't fix their interface.
> 
one of the comments after  I connect is as follows

The VNC desktop is:      localhost:1
PORT=5901

Why is it localhost:1 I thought it should be localhost:0?

TCP port 5900 would be VNC display localhost:0. TCP port 5901 would be VNC display localhost:1, etc.  Maybe you are confused by your -L5900:localhost:5901.  Read the ssh man page on -L to see how it works. 
> 
I would like x11vnc to listen on port 5901 as I want to leave 5900 for vino as a back up. Should I use 
rfbport 5901 or is the autoport 5901 enough?

rfbport 5901 is the best way to force a port.  x11vnc will exit with an error message if it cannot get that port.  With autoport 5901 it tries 5901, 5902, 5903, ... until it finds a free one.  rfbport appears to be better for your usage.

I am out of time; can't address your last question.

---

### Post by 987a654 on 2010-08-11
> **krunge said:**
> Looks reasonable.

Yes.  I suggest "-ncache 10" for the value of n.

will try it out.


> That looks pretty good (except -C-p looks like a typo)

x11vnc listens on 5901 on the remote side, and you point your viewer at localhost:5900 on the local side. 

-C-p is a typo. and I use localhost:5900 on the local side, having it only listen on localhost at least reduces the chance of someone connecting from the internet.

> The -solid option is highly dependent on the desktop being used. For example it has been broken for years on KDE4 and KDE doesn't fix their interface.

I use gnome and it worked first two times and stopped.


> 
rfbport 5901 is the best way to force a port.  x11vnc will exit with an error message if it cannot get that port.  With autoport 5901 it tries 5901, 5902, 5903, ... until it finds a free one.  rfbport appears to be better for your usage.


will use rfbport 5901.

> I am out of time; can't address your last question.

no problem, you have been of great help. Saved me a lot of time.

Thank you

---

### Post by krunge on 2010-08-11
> **987a654 said:**
> 
there's one more thing I would like to get working as well.

I would like to create an additional desktop and connect to it so that we will not have to struggle for the cursor. the following link has some instructions, it's at the end of the page but there is no xstartup file in ~/.vnc/.

Have you run the 'vncserver ...' command yet?  I think it will create one and then you edit it to start the desktop you want.

BTW if you install the 'xvfb' package x11vnc can emulate 'vncserver'.  It is the x11vnc -create option.  But that might be tricky for you to set up and understand so I suggest you try 'vncserver' first to see if it meets your needs.

---

