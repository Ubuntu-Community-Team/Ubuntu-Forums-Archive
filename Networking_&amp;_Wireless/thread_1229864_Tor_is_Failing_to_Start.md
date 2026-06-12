---
title: "Tor is Failing to Start"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by binary010101 on 2009-08-02
Whenever I start Vidalia, it cannot start Tor, saying that "Vidalia detected that the Tor software exited unexpectedly.  Please check the error log for recent warning or error messages."  The error log always says:

Aug 02 17:44:40.240 [Notice] Tor v0.2.1.19. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Aug 02 17:44:40.240 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Aug 02 17:44:40.240 [Notice] Opening Socks listener on 127.0.0.1:9050
Aug 02 17:44:40.240 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Aug 02 17:44:40.240 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Aug 02 17:44:40.240 [Error] Reading config failed--see warnings above.

I also don't know why the Tor package is "experimental software," having followed the installation guide [here]("https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian") to a letter.

---

### Post by Crafty Kisses on 2009-08-02
I'm using Tor, and it works perfectly. I'll try and help you out. First you need to grab the latest stable version of Tor, I'm going to provide the source tarball, this is because this is how I installed it, so run the following:
```
wget http://www.torproject.org/dist/tor-0.2.0.35.tar.gz
```
Then you need to untar it, so run the following:
```
tar xzf tor-0.2.0.35.tar.gz
```
Once you have extracted it, you need to go into the directory, now before you actually go ahead with the initial compile, you need the following package installed, so run as root:
```
apt-get install build-essential
```
Once you have that package installed, you can now run:
```
./configure
make
src/or/tor
```
Now that should take care of Tor. Now you need to install Privoxy, so run as root:
```
apt-get install privoxy
```
Once you have Privoxy, you need to setup a configuration file, so make a filed called "config" in your home directory, make sure it's all lower case it is case sensitive, and put your settings in there, should look similar to this:
```
# Tor listens as a SOCKS4a proxy here:
forward-socks4a / 127.0.0.1:9050 .
confdir /etc/privoxy
logdir /var/log/privoxy
actionsfile standard  # Internal purpose, recommended
actionsfile default   # Main actions file
actionsfile user      # User customizations
filterfile default.filter

# Don't log interesting things, only startup messages, warnings and errors
#logfile logfile
#jarfile jarfile
#debug   0    # show each GET/POST/CONNECT request
debug   4096 # Startup banner and warnings
debug   8192 # Errors - *we highly recommended enabling this*

user-manual /usr/share/doc/privoxy/user-manual
listen-address  127.0.0.1:8118
toggle  1
enable-remote-toggle 0
enable-edit-actions 0
enable-remote-http-toggle 0
buffer-limit 4096
```
Then make sure you have the tor-button plugin on Firefox, or whatever browser you may use, then see if it detects that you're using Tor by going to **[Tor checker]("https://check.torproject.org/")**. If you have any problems, let me know.

---

### Post by hihihi100 on 2009-08-16
Hi there:

Im having exactly this same problem, except that I have followed the instructions found at:

[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

Im not a geek, and I started using ubuntu this month, but I believe that your instructions wont be useful for me, given that I have downloaded and installed deb files, not tar. Correct me if I'm wrong.

If the above is correct, what codes should I write?

Or, what do I have to do?

This is what the log says, exactly the same as the original author of this thread:

Aug 16 22:13:18.500 [Notice] Tor v0.2.1.19. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Aug 16 22:13:18.500 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Aug 16 22:13:18.500 [Notice] Opening Socks listener on 127.0.0.1:9050
Aug 16 22:13:18.500 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Aug 16 22:13:18.500 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Aug 16 22:13:18.500 [Error] Reading config failed--see warnings above.

Thx in advance, please post an explanation for dummies (me)

Almost forgot: this is what the terminal says when pasting your first code:

laptop:~$ wget [http://www.torproject.org/dist/tor-0.2.0.35.tar.gz](http://www.torproject.org/dist/tor-0.2.0.35.tar.gz)
--2009-08-16 22:21:40--  [http://www.torproject.org/dist/tor-0.2.0.35.tar.gz](http://www.torproject.org/dist/tor-0.2.0.35.tar.gz)
Resolving [www.torproject.org](www.torproject.org)... 86.59.21.36
Connecting to [www.torproject.org|86.59.21.36|:80](www.torproject.org|86.59.21.36|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-08-16 22:21:41 ERROR 404: Not Found.

Cheers

---

