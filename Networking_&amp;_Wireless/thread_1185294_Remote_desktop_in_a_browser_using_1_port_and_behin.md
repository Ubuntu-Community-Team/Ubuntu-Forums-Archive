---
title: "Remote desktop in a browser using 1 port and behind a proxy"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by Franic on 2009-06-12
Hi all,

After days of research and tries I still can't get what I'd like to do. Basically what I'd like to do is controlling my home computer from my office using only the HTTPS port (443), from a browser and behind a proxy. Here is what I have:

Home computer
- Kubuntu Jaunty with root privileges (I can install anything I want)
- Apache 2 + SSL support
- Reverse DNS and port forwarding set up correctly (port 443 is redirected to my computer)
I successfully connect to my computer with https from my office, so I guess my Apache setup is OK.

Office computer
- Windows XP SP2 with IE6 (yeah I know...)
- Restricted privileges: basically I can only run a browser
- Java 1.6 is installed (so Java applets work), but not Flash
- Access to WAN is behind a proxy which only allow HTTP and HTTPS (so ports 80 and 443), I use an automatic proxy configuration URL

I've found 3 software which might do it:
- FreeNX
- x11vnc
- TightVNC

But I couldn't get one of them to work the way I want. If anyone knows a way to do it it would be greatly appreciated.

Thanks.

---

### Post by krunge on 2009-06-13
x11vnc can do this.  You will need the Java viewer applet that x11vnc provides.  For some reason debian/ubuntu no longer packages this applet. So you would need to build x11vnc from the source tarball or similar creative thing.  Let me know if you are still interested and I will provide more details.

---

### Post by Franic on 2009-06-15
Yup, I'm totally interested in that. I'd prefer a package than compiling myself (updates are easier this way, and I've never been able to correctly compile any program so far ><) but if I can't avoid it then so be it.

Anyway the Java viewer is OK, I mean Java applets work at my office so there should be no problem. The main problem is it has to support both proxies and SSL.

Thanks for your reply.

---

### Post by krunge on 2009-06-15
> I'd prefer a package than compiling myself (updates are easier this way...

That doesn't really matter because debian hasn't updated x11vnc in two years! Not clear that they will again...

This is too bad because there are some improvements in x11vnc since then that will help with this task.  Since you can't compile (a useful and empowering skill to learn, BTW) maybe you can use a prebuilt binary.

Here is the source tarball to download to get the SSL enabled Java viewer applet:

[indent][http://x11vnc.sourceforge.net/dev/x11vnc-0.9.8.tar.gz](http://x11vnc.sourceforge.net/dev/x11vnc-0.9.8.tar.gz)[/indent]

Download it and unpack it in your home directory, say.  No need to do anything beyond unpacking it.

And here is a pre-built binary that *may* run on your system:

[indent][http://x11vnc.sourceforge.net/dev/x11vnc-0.9.8_TEST_i686-Linux](http://x11vnc.sourceforge.net/dev/x11vnc-0.9.8_TEST_i686-Linux)[/indent]

Download it; rename it to 'x11vnc'; run chmod 755 on it; and then see if you can run it locally like "/path/to/your/x11vnc -V" and "/path/to/your/x11vnc", etc.


The next potential pitfall I see is that since you redirect port 443 on your router to port 443 on your workstation, you would need to run x11vnc as root on the workstation because port 443 is priviledged (i.e. less than 1024.)

Do you know how to redirect port 443 on your router to, say, port 5905 on your workstation? I think that will avoid some headaches if you can do it. Let me know.

BTW, Apache (SSL or otherwise) will not be used in this solution.

---

### Post by Franic on 2009-06-15
Wow, no Apache at all? I'm quite surprised, I mean where is the Java applet hosted then?

I know that compiling programs is a good thing to learn, but besides my own programs there was always something missing, and it was much easier to search for a DEB package or a repository than spending hours to understand why it won't compile ;) But I can compile if I have to and if you tell me which libraries I need :D

For the router thing yes I know how to redirect any port from the outside to any other port on my home computer. My router is quite old but I know how to configure it :)

I can't test it right now because I'm in my office, but once I get back home I'll give it a shot.

Thanks again :)

---

### Post by krunge on 2009-06-15
> Wow, no Apache at all? I'm quite surprised, I mean where is the Java applet hosted then?
x11vnc has a mini http server built-in.  All it has to do is deliver an HTML file and a jar file, and so nothing fancy.  To support HTTPS, x11vnc reuses the code it uses to encrypt VNC with SSL (which uses the openssl library.)
> 
but besides my own programs there was always something missing, and it was much easier to search for a DEB package or a repository than spending hours to understand why it won't compile ;)

Yes, I'm a bit disappointed how difficult distro maintainers make it to compile from source--the hoops they make you jump through for even the most basic stuff. But I will try to stay off of that soapbox.
> 
But I can compile if I have to and if you tell me which libraries I need :D

If that prebuilt binary I pointed you to works, you might as well use that.
> 
For the router thing yes I know how to redirect any port from the outside to any other port on my home computer. My router is quite old but I know how to configure it :)

Good. I recommend redirecting port 443 on the router to port 5905 on the workstation, then we will just have x11vnc listen on port 5905 as you, rather than port 443 as root.  The reason for this is that there is some extra trouble in getting root to  connect to *your* X session that will be avoided by having your userid run x11vnc. BTW, make sure the workstation doesn't block port 5905.


When you mentioned "Proxy" I assume that is a web proxy at your office used for outgoing web connections, right?  In other words, you were not referring to a proxy that you would configure with Apache at your home, correct?

Fortunately x11vnc has a 'proxy.vnc' HTML file set up for the out going web proxy case (which is tricky for a Java applet connecting back via a non-HTTP socket if you think about it.) If you are interested, there are more details here: [http://www.karlrunge.com/x11vnc/faq.html#faq-ssl-java-viewer-proxy](http://www.karlrunge.com/x11vnc/faq.html#faq-ssl-java-viewer-proxy) (it is good background, but we will not be doing everything mentioned in it for this task.)

---

### Post by Franic on 2009-06-15
Yeah, the proxy is a web proxy in my office, at home there's no proxy at all. I'm just back home so give me a little time to try it.

BTW the last link you gave me is exactly what I wanted, geez how come I didn't get this before :sad:

EDIT: the binary runs, and it tells me that it's running without a password (quite annoying...) and the port is 5900. On my router I've redirected the 443 port from outside to port 5900 in my computer. Nmap says that port 5900 on localhost is closed, so I guess it's OK.

---

### Post by krunge on 2009-06-15
> On my router I've redirected the 443 port from outside to port 5900 in my computer. Nmap says that port 5900 on localhost is closed, so I guess it's OK.
OK.  I suggested 5905 to stay clear of any other VNC servers you may (intentionally or not) run on the machine.

Here is a template of a script I suggest to run it.  You will need to edit the paths to reflect what is on your machine:
```

#!/bin/sh
#
# Filename: go_x11vnc
#
# We assume everything is in /home/franic.  I.e. the x11vnc binary
# is /home/franic/x11vnc and the x11vnc source is unpacked into
# /home/franic/x11vnc-0.9.8  If not, change the paths below.
#
# To connect through a web proxy enter this URL into the browser:
#
#       https://your.host.or.ip/proxy.vnc
#
# where it is assumed port 443 on the router (your.host.or.ip) is
# redirected to port 5905 on the workstation (make sure port is not blocked.)

/home/franic/x11vnc \
        -ssl SAVE \
        -httpsredir \
        -httpdir /home/franic/x11vnc-0.9.8/classes/ssl \
        -rfbport 5905 \
        -forever \
        -passwd myword \
        -logappend /home/franic/x11vnc.txt

```
In case you (or others reading) don't know how to create and run a shell script, save the above in a file, say /home/franic/go_x11vnc and then in a terminal type "chmod 755 /home/franic/go_x11vnc" and then type "/home/franic/go_x11vnc" to run it.

The output messages for troubleshooting will appear in "x11vnc.txt"

Be sure to heed the suggestions under 'Tips on Getting the SSL Java Applet Working the First Time' here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-ssl-tunnel-viewers](http://www.karlrunge.com/x11vnc/faq.html#faq-ssl-tunnel-viewers)[/INDENT]

The **MOST IMPORTANT ONE** I paste in here:

[INDENT]Always Restart the Browser: If you are having failures and have to repeatedly retry things ALWAYS restart the browser (i.e. completely exit it and then start a new browser process) each time. Otherwise as you are changing things the browser may "remember" failed applet downloads, etc. and just add to the confusion and irreproducibility. If you see it trying to download VncViewer.class (instead of VncViewer.jar) you know it is really confused and needs to be restarted.[/INDENT]

it will save you a lot of time and confusion if you fully restart the web browser for each new test.

Good luck.

---

### Post by Franic on 2009-06-15
Thanks a lot for the shell script (well I know how to make and run these, but it doesn't hurt in case it's useful for others). 

Now I use the 9505 port as you advise. I changed the permissions as you said (chmod 755 go_x11vnc) but I get an error if I run it as an user (ssl error: error:0200100D:system library:fopen:Permission denied). If I run it with sudo there's no error. 

Now it's running (with sudo), I'll see how it shows at work tomorrow (I have a *weird* bug that I can't add self-signed SSL certificates exceptions on websites hosted on localhost, but it's another matter). Thanks again for your help, it's greatly appreciated.

---

### Post by krunge on 2009-06-15
> Tbut I get an error if I run it as an user (ssl error: error:0200100D:system library:fopen:Permission denied). If I run it with sudo there's no error. 

Now it's running (with sudo), I'll see how it shows at work tomorrow

Hmmm, this doesn't sound good.  There is no reason it shouldn't run correctly as the user who is logged into the X session desktop.

I assume your userid is logged into the current X session and you run the 'go_x11vnc' script from a terminal inside that X session and from inside a directory where you have write permission.  Is this correct?

I think your 'fix' with sudo is masking a larger problem that will lead to failures later. (e.g. that it happens to find your X session is pure luck.)

Before you go into work why not test it locally on your LAN.  That could save a day or two.  If you have, say, a laptop (any OS) also on your home network you could try connecting from there: "https://workstationname:5905".  Or try connecting to "https://localhost:5905" from the same Xsession (this will cause infinite recursion / barbershop mirrors effect, but you can X-out the viewer window quickly.)

If you don't understand what I mean by testing it out locally just ask.

---

### Post by Franic on 2009-06-16
I'm now at work (it's OK if it takes some time to work, don't worry I'm not that hasty ;) ), and I can connect to my home computer but as expected it uses the root's desktop, not mine. So the sudo "fix" is not a good fix at all :p And I get a java.io.IOException once I submit my proxy settings.

My username is franic, I'm logged as franic and the script is in /home/franic/go_x11vnc so I have write permissions. And yes I'm running it in a terminal. To run it I run the terminal, I type cd, I press Enter and I type ./go_x11vnc and press Enter.

I'd love to test it locally (actually I've tried many times) but I don't know why Firefox won't let me add an exception for the self-signed certificate (I can with WAN websites, but not on localhost). It is the same if I host my website on Apache2 as well, so as long as I still have this *bug* I can't test it on localhost.

Once I'm back home I'll paste the complete log and the screenshot for the certificate bug, maybe it'll help.

Thanks again.

EDIT: Here is my x11vnc.txt when go_x11vnc is run without sudo: [http://pastebin.com/m6a89dc34]("http://pastebin.com/m6a89dc34")
And the error when I try to access to localhost with https: [IMG]http://wisdomfranic.free.fr/data/unix/ssl_localhost_firefox.png[/IMG] (too bad it's in French)
A translation would be:

locahost:5905 is using an invalid security certificate.

The certificate is not safe because it's self-signed.
The certificate is only valid for <a id="cert_domain_link" title="x11vnc-SELF-SIGNED-
CERT-28224">x11vnc-SELF-SIGNED-CERT-28224</a>

(Error code:sec_error_ca_cert_invalid)

---

### Post by krunge on 2009-06-16
For testing locally, have you tried this?

[indent][https://192.168.X.Y](https://192.168.X.Y)[/indent]

Where 192.168.X.Y is meant to be your workstation's ethernet IP address (the command "/sbin/ifconfig -a" should reveal it.)


Given the x11vnc.txt text you uploaded, to fix the permissions problem I suggest clearing out the .vnc directory where x11vnc keeps things and trying again:
```
sudo rm -rf /home/franic/.vnc
```
You problably also need to remove /home/franic/x11vnc.txt (via sudo) before trying again.

Then be sure to *never* run x11vnc as root again until we get it working as your userid (actually, once we get it working I see no need to run x11vnc as root)

So after you clear out /home/franic/.vnc and x11vnc.txt, run go_x11vnc again as user 'franic'.

---

### Post by Franic on 2009-06-16
Oh my god I never thought the localhost bug was that simple to get rid of... thanks a lot I can now test it on localhost :D

I did what you asked (removed the folder $HOME/.vnc and x11vnc.txt) and now I can run ./go_x11vnc as an user. It's getting close ^^

EDIT: Ok it's getting closer but I think that the password was missing. So I ran > x11vnc -storepasswd
 and typed my password (the same that I use to log in, but that may not be useful) then I changed the script a little in order to tell where the password is stored. So now the command is > /home/franic/x11vnc \
        -ssl SAVE \
        -httpsredir \
        -httpdir /home/franic/x11vnc-0.9.8/classes/ssl \
        -rfbport 5905 \
        -forever \
        [COLOR="Red"]-passwdfile ~/.vnc/passwd[/COLOR] \
        -logappend /home/franic/x11vnc.txt
 
I checked and file ~/.vnc/passwd really exists and has data. Now it's running without sudo, but I can't log in (it says authentication fails). Here is the log: [http://pastebin.com/m1a8d5c31]("http://pastebin.com/m1a8d5c31")

I'll check it at work, maybe it'll work fine there :)

---

### Post by krunge on 2009-06-16
> Ok it's getting closer but I think that the password was missing. So I ran  and typed my password (the same that I use to log in, but that may not be useful) then I changed the script a little in order to tell where the password is stored. So now the command is  
I checked and file ~/.vnc/passwd really exists and has data. Now it's running without sudo, but I can't log in (it says authentication fails).

No, what you are doing with the password is incorrect.  You should follow my instructions to the letter and not cook up your own stuff ;-)

If you create a VNC password with '-storepasswd' you should point x11vnc to it via '-rfbauth' not '-passwdfile' This is pretty clearly stated in the x11vnc documentation.

The -passwdfile is if you want to supply a plain ascii text password in a file.  But you pointed -passwdfile to the binary data file ~/.vnc/passwd and so those binary characters are the expected password!!!  This is why the login failed, you typed in something quite different from those binary characters.

**Good news:** I looked at your paste.bin log and it reveals a perfect connection.  However since you didn't follow my instructions and set up the password incorrectly it didn't let you in because you supplied the wrong password.

I suggest using what I had in the script I sent you "-passwd myword" (replace "myword" with whatever password you want.)  Once you get that working you can change it to -rfbauth or -passwdfile.


So I claim your local test should work perfectly once you do this.  Then we are on to the Web Proxy case from your work. This is actually the tricky part of the journey.

**Important:** if you are having trouble connecting from work, be sure to capture and post to paste.bin the full Java Console output in addition to the full x11vnc.txt output.

BTW here is example Java Console and x11vnc output for the Web Proxy case:

[INDENT][http://www.karlrunge.com/x11vnc/java_console_proxy.html](http://www.karlrunge.com/x11vnc/java_console_proxy.html)[/INDENT]

Good luck.

---

### Post by Franic on 2009-06-17
Sorry I thought that the password had to be stored in a file (with some kind of encryption like in Unix) rather than directly as an argument in the script (talk about security issue... oh well) sorry again. If it works on localhost that's perfect.

The proxy is quite disturbing because I can't even supply my password. I get a java.io.IOException once I supply my proxy settings. The point is I use an automatic proxy configuration URL, which is simply a text file. I've retrieved the IP address and port which seem to be used when I try to connect to home but no luck. 

What's really surprising me is the tracert DOS command works when I try to reach home, but the IP that should be used as proxy is not displayed. Maybe I lack some network knowledge...

This evening I'll try to make a symbolic link from the http server to x11vnc.txt at home so that I can read it from work, maybe it'll help.

Thanks again, and sorry for my mistake ;)

EDIT: Damn the proxy really is bugging me, I've activated the Java Console and here is what I have once my proxy settings are supplied (I've removed the true IP address and port in my code):
```
User said host: a.b.c.d port: abcd
proxy_in_use psocket:
psocket prob: access denied (java.net.SocketPermission a.b.c.d:abcd connect,resolve)
1-a sadly, returning a null socket
java.io.IOException
java.io.IOException
	at RfbProto.<init>(RfbProto.java:214)
	at VncViewer.tryAuthenticate(VncViewer.java:311)
	at VncViewer.connectAndAuthenticate(VncViewer.java:296)
	at VncViewer.run(VncViewer.java:170)
	at java.lang.Thread.run(Unknown Source)

```

Update: I think I got what's blocking, and it doesn't look good :( At work, when I try to connect to a website with Google Chrome or Opera the browser asks me my login and password in order to use the proxy. At work we use NTLM (basically the login is domain\username and the password the one I give in order to log in my session). So maybe the proxy needs my login and password, but the Java applet doesn't support NTLM so it fails. I really hope it's not the case, or I don't know how to bypass it...

---

### Post by krunge on 2009-06-17
> Sorry I thought that the password had to be stored in a file (with some kind of encryption like in Unix) rather than directly as an argument in the script (talk about security issue... oh well)
There a number of options for the password once you get this working.  I suggested the '-passwd' since that is the easiest way to get it to work. Also, I assumed there were no untrusted users on your home machine.
> 
What's really surprising me is the tracert DOS command works when I try to reach home, but the IP that should be used as proxy is not displayed. Maybe I lack some network knowledge...

tracert doesn't use a web proxy. It is just a normal app that uses the network.
> 
This evening I'll try to make a symbolic link from the http server to x11vnc.txt at home so that I can read it from work, maybe it'll help.

You are running your http server on port 80, correct?  (https port 443 obviously won't currently work)
> 
EDIT: Damn the proxy really is bugging me, I've activated the Java Console and here is what I have once my proxy settings are supplied (I've removed the true IP address and port in my code):
...
Update: I think I got what's blocking, and it doesn't look good At work, when I try to connect to a website with Google Chrome or Opera the browser asks me my login and password in order to use the proxy. At work we use NTLM (basically the login is domain\username and the password the one I give in order to log in my session). So maybe the proxy needs my login and password, but the Java applet doesn't support NTLM so it fails. I really hope it's not the case, or I don't know how to bypass it...

Oh, a proxy with a password?  I've never seen one of those. That could be tricky.

Please mail me the entire Java Console output. There is no need to edit any of the strings for privacy since I don't care.  If you feel you must censor the console output please do it realistically.  E.g. I assume "a.b.c.d" above were numbers, right?  Please don't do things that leave me guessing.  Sending the entire unedited Java Console is best. xvml AT karlrunge.com

---

### Post by krunge on 2009-06-17
A few additional notes.
> 
What's really surprising me is the tracert DOS command works when I try to reach home, but the IP that should be used as proxy is not displayed. 

Are you saying tracert can reach your home directly?  If so, maybe the java viewer does not need to use a web proxy. Can you telnet (Windows used to include a telnet client, not sure if it does anymore.) to your home machine's port 80 or port 443?  E.g. from a windows CMD shell:
```

telnet your.ip.addr 80
telnet your.ip.addr 443

```


One other thing.  What URL do you type into the Web browser?  You didn't say. For Web Proxy usage it should be:
[INDENT][https://your.ip.addr/proxy.vnc](https://your.ip.addr/proxy.vnc)[/INDENT]
while for a direct connection it should be:
[INDENT][https://your.ip.addr](https://your.ip.addr)[/INDENT]
Also a trick to use a direct connection and force the java viewer to not even check for a web proxy is:
[INDENT][https://your.ip.addr/?ignoreProxy=yes](https://your.ip.addr/?ignoreProxy=yes)[/INDENT]

---

### Post by Franic on 2009-06-17
Sorry for the IP I removed, it's only because these are from my company. Of course my letters are in fact numbers, it's like 10.2.3.4:8005.

To connect to my applet I simply used [https://myip](https://myip). I've tried [https://myip/proxy.vnc](https://myip/proxy.vnc), and I have a different error
```
Network Error: Remote host closed connection during handshake
```

For the tracert I can't reach my computer, but it goes outside I'm sure of it (it uses routers only my ISP have). The telnet doesn't work at all.

For the symbolic link I just thought I could put a symbolic link in the same folder as proxy.vnc, so I could use it with port 443 as well. I don't see why it won't work... and at home it works, I have my log in Firefox.

I'm not allowed to send external emails at work, so I'll use pastebin again.

---

### Post by krunge on 2009-06-17
> 
For the symbolic link I just thought I could put a symbolic link in the same folder as proxy.vnc, so I could use it with port 443 as well. I don't see why it won't work... and at home it works, I have my log in Firefox.

Apache web server usually has to be configured to Follow-Symlinks.

Anyway, the x11vnc.txt log is not so useful since we can't get past the proxy.  You definitely downloaded the Applet OK; that will be the only thing in x11vnc.txt
> 
UPDATE: here is the complete log with untouched informations. And it really seems it uses NTLM authentication... ouch.
Because it has some informations about my company, I'll delete it once we get what's wrong :)

I got a copy of it so you can delete if you would like to.

Boy, NTLM Web proxy authentication... I've never dealt with any Web proxy needing a password so I will have to think about this.  I told you the Proxy would be the tricky part of the journey...

---

### Post by Franic on 2009-06-17
Thanks again (I removed the pastebin link), wow I didn't expect it to be that tricky. It may be useful but we use NTLMv1 so far, but we'll soon switch to NTLMv2 so I have to find a way that works for both of them.

I'll do some research as well, I still hope there's a way to bypass it :)

---

### Post by krunge on 2009-06-17
> Wow I didn't expect it to be that tricky. It may be useful but we use NTLMv1 so far, but we'll soon switch to NTLMv2 so I have to find a way that works for both of them.

It is tricky because the viewer applet can't use a HTTP connection to tunnel the VNC  traffic.  Otherwise applet could borrow HTTP connection services from your browser.

Actually in theory it should be possible to tunnel any socket traffic through two HTTP connections (one send the other receive) but that would be horrendous.

I note in the output:

[indent]
Proxy-Authenticate: NTLM
Proxy-Authenticate: BASIC realm="...."
[/indent]
This seems to suggest Auth-BASIC (very easy to implement, just send the username+password base64 encoded) is available as well.   Would you be willing for the x11vnc SSL VNC viewer to try Auth-Basic in this circumstance?

---

### Post by krunge on 2009-06-18
> This seems to suggest Auth-BASIC (very easy to implement, just send the username+password base64 encoded) is available as well.   Would you be willing for the x11vnc SSL VNC viewer to try Auth-Basic in this circumstance?

I just uploaded a new tarball:

[indent][http://x11vnc.sourceforge.net/dev/x11vnc-0.9.8.tar.gz](http://x11vnc.sourceforge.net/dev/x11vnc-0.9.8.tar.gz)[/indent]

whose java viewer applet supports "Proxy-Authenticate BASIC" (works OK for me.) I tested it using Apache as a web proxy requiring a username+password.  An ugly popup appears at the appropriate time that asks for your web proxy username+password.

I suggest trying it. Just unpack the new tarball in the right place.

---

### Post by Franic on 2009-06-18
Ok thanks a lot I'll try it once I'm back home. I don't care if I have to send my username and password as long as it works :)

Browsers besides IE (which can retrieve the username and password from the Windows session) ask them as well, so it's kinda normal that I need them to bypass the proxy. Even if your popup is ugly I'm still happy :D

---

### Post by krunge on 2009-06-18
> Ok thanks a lot I'll try it once I'm back home. I don't care if I have to send my username and password as long as it works.

Doing that proxy authentication via NTML is a little more secure than using BASIC.  But the proxy offers BASIC so I assume we can use it.  BTW, the proxy login dialog network traffic is all inside the company so I assume that is why they allow BASIC.

---

### Post by Franic on 2009-06-19
You're truly awesome, it works perfectly!!! I can't believe you added such a nice feature so quickly, and it really works :popcorn: :)

Ok next steps (but I think I can manage them, I'll have the whole week-end for that), store my password in an encrypted text file and store the proxy parameters directly inside the .vnc page. Anyway you've done a lot for me, thanks a million :D

BTW do you mind if I share this topic in the French ubuntu forum? There is no thread about vnc with ssl and proxy, and I'm sure there are people who'd like to do the same as me (at least I have a colleague who's interested). Of course I'll give you the credits :)

---

### Post by krunge on 2009-06-19
> You're truly awesome, it works perfectly!!!

Great, glad to hear it is working with the proxy login.
> 
Ok next steps, store my password in an encrypted text file

FYI, If you mean the VNC password in ~/.vnc/passwd (created, e.g. by x11vnc -storepasswd), it is not really encrypted.  It is just obscured to not be plain text. VNC doesn't have an encrypted pw format, and if it really was encrypted you'd need to supply a passphrase to unlock it.
> 
BTW do you mind if I share this topic in the French ubuntu forum? There is no thread about vnc with ssl and proxy, and I'm sure there are people who'd like to do the same as me (at least I have a colleague who's interested).
Sure. One thing I am disappointed with this thread is that it now contains too much entropy.  Initially I had hoped this thread would be a concise solution to the (challenging) problem you posed.  But between the normal false starts and the proxy authentication twist, I don't think anyone will wade through all we have written. Do you think you could start a new thread in this forum that concisely describes the steps needed? I like the title you chose for this thread, maybe just add "How to:" or "Solution:" to the front. Anyway, thanks if you can do that.

---

### Post by Franic on 2009-06-19
Ok sure I'll try to make a clean howto when I've some time left that's the least I can do, I'm sure it will be useful for some people ^^

---

### Post by krunge on 2009-06-19
> ... and store the proxy parameters directly inside the .vnc page.
That's another useful proxy feature your usage has suggested.  Earlier today I uploaded another x11vnc-0.9.8 tarball that enables it.  See the classes/ssl/README file for the description of proxyHost and proxyPort parameters. I also modified the behavior of the existing forceProxy parameter.

---

