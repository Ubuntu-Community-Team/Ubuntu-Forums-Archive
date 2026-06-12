---
title: "HOWTO: Setup mldonkey server and GUI client on separate machines"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by nickzeff on 2008-02-02
I couldn't find a good HOWTO on this, so I thought I'd help out those who want to set up a good p2p system where the client is separate from the server.

I like this setup, since the server daemon runs on my Ubuntu server which is always switched on. The client is on my laptop, so I can connect in any time I like to see how things are going, but can easily power down since all the hard work is being done remotely..

OK. So there are two major parts here. Setting up the server and setting up the client.

**PART ONE: SERVER**

I have Ubuntu Server Gutsy, so not sure how this runs on previous versions.

**1. Installation**

Open a terminal on your server machine, or ssh over there from the client. Then install donkey server from the repos with

sudo apt-get install mldonkey-server

When it asks if you want to auto-start at startup, say yes.


**2. Allowing client connections**

You now need to explicitly tell the server which IPs are allowed to connect. Before you can modify any conf files, ensure the daemon is not running by typing

sudo /etc/init.d/mldonkey-server stop

Now in your favourite text editor, open /var/lib/mldonkey/downloads.ini. For me that means

sudo vim /var/lib/mldonkey/downloads.ini

Scroll down the file until you get to the allowed_ips parameter. Both the client and server machines I use are on my own LAN, so I'm happy to be generous with my allowed IPs. That means that I modified the line from:

 allowed_ips = [
  "127.0.0.1"; ]

to:

 allowed_ips = [
  "127.0.0.1";
  "192.168.1.0-192.168.1.255";]

Allowing any machine on my lan with an IP address between 192.168.1.0 and 192,168.1.255 to connect.

You'll have to do the research and work out what IPs your client machine(s) have. If they're static, you're set. If they're assigned dynamically by DHCP by your router, you'll have to work out what the range is.

There are lots of other settings in the downloads.ini file, so you might want to have a scan through - it's quite well documented in there.

Save the file and get back to the prompt. Start the daemon with

sudo /etc/init.d/mldonkey start


**3. Everything running?**

You can check that the service is now running, by using a telnet client connection to the server. While still on the server machine, type:

telnet 127.0.0.1 4000

This should start the telnet client with a "Welcome to MLDonkey" message. You can quit the client by typing "q" with a carriage return.

If you get a "Connection Refused" message, the daemon probably hasn't started properly.
 
You can check to see that everything is ok by having a look at the log:

tail /var/lib/mldonkey/mlnet.log

Or indeed checking that the daemon is running with:

ps -u mldonkey

This should return a line showing that the process is running. This was useful for me to know, since I initially got the allowed_ips syntax wrong in the ini file which meant the daemon wasn't starting (doh!)

Once you've confirmed the service is up and running, it's time to get connecting from your client machine.


**PART TWO: CLIENT**

I have Ubuntu (Desktop) Gutsy on my client machine.

**1. Initial connect and setup**

Check you can connect from your client by going into a terminal and typing:

telnet <server> 4000

where <server> is the IP or name of the machine where you just installed the server.

If you get an allowed_ips error, you've probably set up the ini file wrong, so go back and amend the file on the server, remembering to stop the daemon first, otherwise your changes won't get saved.

If you get in to the client, you can log in by typing

auth admin

This will get you in, but you'll get a warning that admin has a blank password and you should change it. You can do this by typing

passwd <new_password>

Where <new_password> is an exciting and mysterious word of your choice.

Leave the terminal open - we'll probably need it again in a minute.


**2. Installing the GUI**

You can install the mldonkey-gui through aptitude or just open another terminal and type

sudo apt-get install mldonkey-gui

This will get everything installed.


**2. Connecting from the GUI**

Find MLDonkey on your menu under "Internet".

On the status bar at the bottom you can probably see it says "Not Connected". Click these words, and a menu will appear. Choose the "settings" option and go to the interfaces tab. The fields you need to fill in are

"Password" - set this to the password you just used above
"Hostname" - your server IP or machine name
"Login" - set this to "admin"

Click "OK" at the bottom, then try connecting via the same menu.

This should now connect ok.You'll see the status change.


**3. Where's my server list?**

When you now click on the "Servers" button, you get a blank screen with no servers. Or at least I did. The only way I could figure out how to update this was through the telnet client rather than the GUI.

Before you do that, open a web browser and browse to

[http://ed2k.2x4u.de/index.html](http://ed2k.2x4u.de/index.html)

On the line that says "all servers", right click the "server.met" link to get its properties. It's probably going to be something like:

[http://ed2k.2x4u.de/brkity5e/max/server.met](http://ed2k.2x4u.de/brkity5e/max/server.met)

But they change every 10 minutes or so. Copy this to your clipboard.

Now head back into the terminal with the telnet session still open to the mldonkey server. Type:

servers <pasted_url>

Where <pasted_url> is the url you just copied to the clipboard.

It should now process the met file and get you a list of servers in your GUI client. If it hasn't worked, you can always check the log on the server (see above). There is a chance the URL has expired, so refresh the page in your browser and get the link properties again.


And that's about it!

There's loads more you can do, but I hope I've given someone a good idea of the basics here. Good luck!

---

