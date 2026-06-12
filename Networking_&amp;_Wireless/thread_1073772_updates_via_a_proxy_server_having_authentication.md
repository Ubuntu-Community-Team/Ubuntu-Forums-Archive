---
title: "updates via a proxy server having authentication"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by necronwarrior on 2009-02-18
I am having problem updating my ubuntu 8.10 through the internet due to a proxy server.Also synaptic or any other system task that connects to the internet wont work.
the error when i try to run apt-get in terminal is--
(the full error is mainly a repetion of the following lines-)

Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) intrepid-updates/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) intrepid-updates/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://cudlug.cudenver.edu/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://cudlug.cudenver.edu/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

I have tried adding 
export http_proxy=http://user:password@my.proxy.server:port/
export ftp_proxy=http://user:password@my.proxy.server:port/

to the etc\bash.bashrc file but still i get the same error.

I have also input the proxy configuration and authentication in "SYSTEM-->PREFEPRENCES-->NETWORK PROXY"

Firefox works just fine with the proxy which asks for authentication each time i try to open a site. 

I also cant run Limewire,vuze,pidgin.
I think the problem is with the password for the proxy server ---- it contains a "@".(might also be the username-----contains a "\")

PLEASE HELP!!

---

### Post by waffen on 2009-03-25
I have the same issue, but my user name dont have the @ or \ is very simple... I think is a Ubuntu problem...

---

### Post by necronwarrior on 2009-03-30
I have found the solution to the  problem............(i am not sure if you are having the same problem)(do you have a ISA proxy server. This solution will work only for ISA servers)
It's not a ubuntu problem but a problem at authentication system for the the ISA proxy server.
To get through it you need download NTLM (NTL maps).(download it here [http://sourceforge.net/projects/ntlmaps/](http://sourceforge.net/projects/ntlmaps/))
First edit the server.cfg(use any text editor) file to enter your proxy ip address,domain name(the part of the user name before "\"),your user name(the part after the "\")  and your password.(all these fields are clearly mentioned in the server.cfg file).
Now run a terminal and navigate to the directory where the NTLM is extracted and run the main.py fle by typing "python main.py" (without quotes).
It will give a message--
 [U]NTLM authorization Proxy Server v0.9.9.0.1
Copyright (C) 2001-2004 by Dmitry Rozmanov and others.
Now listening at Nightbringer on port 5865
[/U]DONOT CLOSE THE ABOVE WINDOW!!!
Now open up another terminal window and export the http_proxy variable to point to the local loopback address([http://127.0.0.1](http://127.0.0.1)) at the port specified in the message given by the main.py script
for eg the default command should be 
export http_proxy=http://127.0.0.1:5865
Now you can run updates etc. the usual way . For eg. 
sudo apt-get update

If you get an error saying "unable to create socket on port XXXX ..." just edit the server.cfg file and change the port no. in the first line and then run main.py again.
For a more detailed version on the above process(also for windows) and a video tutorial visit the link:  [URL="http://ankurs.com/2009/02/ion-proxy-login-problem/"]
[/URL][http://ankurs.com/2009/02/ion-proxy-login-problem/](http://ankurs.com/2009/02/ion-proxy-login-problem/)

---

### Post by necronwarrior on 2009-03-30
The problem with torrents and limewire is that the proxy server has blocked all peer to peer connections.
Another restriction is that the server refuses to let me login after 12:29 am uptill 5:30 am.
DOES ANYBODY HAVE ANY IDEA AS TO HOW THIN LIMITATION MAY BE REMOVED OR A WORKAROUND??????
i am really pissed at not being able to download torrents..... :-( :-(:-( :-(:-( :-(:-(

---

### Post by siddverma96 on 2009-07-17
Even im using the ion connection...... anyone knows how to fix **torrents**....
neeed serious help!!! its really frustating....

(btw what are you mit computer guys doing??? ur supposed to know all this right? plz develop a workaround fast... even im trying hard!)

---

