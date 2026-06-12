---
title: "How do I set up a local server in Ubuntu?"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by EpicTTR on 2011-09-23
Sorry if I seem to be a bit nooby, I'm fairly new to Ubuntu and this is my first post (so this might be the wrong section).

Anyways, I'm running Windows on one of my computers (not this one, I'm on my MacBook right now), anyways, I've run Ubuntu in a virtual machine before, and here's what I want to do.

I want to set up a (web) server on Ubuntu in the virtual machine, it'd just host a single website and preferably it'd only be accessible by my network (effectively my virtual machine and my real Windows machine). Would it some how be possible to set up such a website? That's running off my virtual machine, accessible to my Windows machine? It wouldn't need a domain name or anything, and I'd only need to run it for five minutes or less. I've seen it done before, but I have no idea how.

---

### Post by dreamsR4living on 2011-09-23
There are several ways to be able to use Ubuntu as a local webserver.

The "official" way to do it is to install LAMP (Linux Apache MySQL PHP). You should check the official documentation on how to do it.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Down below I wrote down the most important steps for you.

I hope you are a little bit familiar with the terminal.

If you are running Ubuntu 11.04 you should execute the following command in terminal first, it is not needed for older versions of Ubuntu;

```
sudo apt-get install tasksel
```

The next step is to run;

```
sudo tasksel install lamp-server
```

When this step has been completed, your LAMP sever is installed.

With your web browser, go to the URL [http://localhost](http://localhost) : if you read "It works!", which is the content of the file /var/www/index.html , this proves Apache works.

You should put your website's files in the /var/www/ directory. Replace the index.html file which is already there with your own index.html file.

To put your index.html file in /var/www/ you could use the following methods;

Move a single file by terminal;

```
sudo cp /path/to/your/file /var/www/
```

Move multiple files and folders by terminal;

```
sudo cp -R /path/to/your/files /var/www/
```

Or you could use your graphical (nautilus) filemanager to just copy paste your files, like you normally would in the graphical user interface. When you copied the files, open the terminal and type; 

```
sudo gnome-open /var/www/
```

The filemanager wil now open with root access, so you are able to paste your copied files.

When you placed your files in /var/www/ they should be visible in your webbrowser when you type [http://localhost](http://localhost). You should place index.html directly into /var/www/. If you put it in another folder inside /var/www/, like for example; /var/www/website/index.html, you should type [http://localhost/website](http://localhost/website) in your browser to access it.

I do not know a lot about local networks, so I cannot tell you if you website will also be accessible by typing [http://localhost](http://localhost) in the webbrowser of other computers in your network.

If these steps above don't seem to work for you, you should check out XAMPP;

[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

Good luck!

---

### Post by EpicTTR on 2011-09-23
> **dreamsR4living said:**
> There are several ways to be able to use Ubuntu as a local webserver.

The "official" way to do it is to install LAMP (Linux Apache MySQL PHP). You should check the official documentation on how to do it.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Down below I wrote down the most important steps for you.

I hope you are a little bit familiar with the terminal.

If you are running Ubuntu 11.04 you should execute the following command in terminal first, it is not needed for older versions of Ubuntu;

```
sudo apt-get install tasksel
```

The next step is to run;

```
sudo tasksel install lamp-server
```

When this step has been completed, your LAMP sever is installed.

With your web browser, go to the URL [http://localhost](http://localhost) : if you read "It works!", which is the content of the file /var/www/index.html , this proves Apache works.

You should put your website's files in the /var/www/ directory. Replace the index.html file which is already there with your own index.html file.

To put your index.html file in /var/www/ you could use the following methods;

Move a single file by terminal;

```
sudo cp /path/to/your/file /var/www/
```

Move multiple files and folders by terminal;

```
sudo cp -R /path/to/your/files /var/www/
```

Or you could use your graphical (nautilus) filemanager to just copy paste your files, like you normally would in the graphical user interface. When you copied the files, open the terminal and type; 

```
sudo gnome-open /var/www/
```

The filemanager wil now open with root access, so you are able to paste your copied files.

When you placed your files in /var/www/ they should be visible in your webbrowser when you type [http://localhost](http://localhost). You should place index.html directly into /var/www/. If you put it in another folder inside /var/www/, like for example; /var/www/website/index.html, you should type [http://localhost/website](http://localhost/website) in your browser to access it.

I do not know a lot about local networks, so I cannot tell you if you website will also be accessible by typing [http://localhost](http://localhost) in the webbrowser of other computers in your network.

If these steps above don't seem to work for you, you should check out XAMPP;

[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

Good luck!

Alright, but the thing is, I want to be able to access it from other computers in my network (even if they're actually on the same physical computer)... do you know of any way to do that? Or would I just have to host it completely online?

---

### Post by drdos2006 on 2011-09-23
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing webserver.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

