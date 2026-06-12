---
title: "incoming vpn on 10.10?"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by darkenedday on 2011-02-19
so let me first say that I am very impressed with how far ubuntu has come, it has been only a year since I last ran ubuntu and it's improved by leaps and bounds. Wine is still dissapointing however (I know totally unrelated to the OS) but virtualization is coming alone GREAT, currently I am typing this in a windows 7 x64 VM, launched from an icon on my desktop and the dc universe online client is downloading the game in the background. AWESOME
      now for my question, as I said it's been awhile since I used linux of any sort and I have a certain thing that I need to set up and have working and have absolutely no idea how. I am an American living in europe for a short time and on windows I had an incoming vpn connectio set up so that family back in the states could access my computer and NAS on my LAN, they all run windows (except my mother who's computer I set up with kubuntu 10.04 after she kept complaining about "viruses" in windows and how it kept breaking) and I was wondering how I could set up this incoming vpn so that the windows users back home could connect to my LAN through this computer and be able to access my NAS on the same network and subnet. This is quite important to me does anyone have any idea how I would go about this?

thanks much!
darkenedday

---

### Post by SeijiSensei on 2011-02-19
One possibility is to run the Apache web server on the Ubuntu box and share the NAS over the web.  You can enforce access controls with passwords as well.  The biggest advantage to this method is that the remote users need nothing beyond a web browser to access the NAS.

If you want a real VPN solution, there are two options I can suggest.  The less secure option is to install the [pptpd]("http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html") daemon in Ubuntu which supports the ancient PPTP VPN protocol in Windows.  The more robust solution is [OpenVPN]("http://openvpn.net/"), but it requires that client software be installed on the Windows machines and may not be as easy to configure as PPTP.

Still unless you have a real need for the remote users to actually be on your network, as opposed to simply accessing the NAS, I'd vote for the web server approach as the simplest soltuion.

---

### Post by darkenedday on 2011-02-19
sounds simple enough, problem is where do I get apache? and is there a GUI rather than just a CLI? I'm fine with either way just prefer not having to learn a new set of commands.

EDIT: found the package name is apache2, got it installed as well as webmin for a nice browser based gui, problem is I can't figure out how to mount the network drive in a permanent location to be able to share it with apache. . . working on that now, will post when I find it, otherwise any help is much appreciated.

---

### Post by SeijiSensei on 2011-02-19
Mount the drive manually in /etc/fstab to a fixed mount point.  How you do this depends on the file system on the drive.  Many drives comes with either FAT32 or NTFS file systems.  

First create a mount point for the drive like this 

```
sudo mkdir /media/NAS
sudo chmod 0755 /media/NAS
```

Then edit (as root) /etc/fstab to add a line like this:

```
/dev/sdb1    /media/NAS     vfat     defaults     0 0
```

assuming the external device is formatted as FAT32 and appears as /dev/sdb1.  If it's an NTFS device, the options are a bit trickier.  See [https://help.ubuntu.com/community/MountingWindowsPartitions#Manual%20Configuration](https://help.ubuntu.com/community/MountingWindowsPartitions#Manual%20Configuration).

I'd use an "[Alias]("http://httpd.apache.org/docs/current/mod/mod_alias.html#alias")" directive in Apache to reference the drive.  Add a line to /etc/apache2/sites-enabled/000-default like this:

```
Alias     /files     /media/NAS
```

Then the URL [http://server/files](http://server/files) will point to the NAS.

---

### Post by darkenedday on 2011-02-19
turns out the dns-321 from dlink actually uses ext3 (or at elast thats what I got from the manual) I have it mounted to /home/mike/mediashare now, problem I am having is figuring out how to get the directory to show at myaddress/mediashare. . .

EDIT: so I added the line as you said, however i go to 192.168.0.101/mediashare and still it says that this page does not exist. . . going to simply 192.168.0.101 shows the "It Works!" message. . . at this point I am stumped, sill researching though. thanks for the help and if you have any more advice i'd certainly like to see it. 

the line I added looks like this:
Alias /mediashare /home/mike/mediashare

---

### Post by darkenedday on 2011-02-19
here is that whole config file

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
    Alias /mediashare /home/mike/mediashare
	<Directory /var/www>
         Options Indexes FollowSymLinks
        </Directory>
</VirtualHost>

---

### Post by SeijiSensei on 2011-02-19
Sorry.  I forgot to mention you need to create a <Directory> stanza for the aliased directory.

```

Alias /mediashare /home/mike/mediashare

<Directory /home/mike/mediashare>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>

```

You may want to require [authentication]("http://httpd.apache.org/docs/2.2/howto/auth.html").  You might also want to create a [self-signed SSL certificate]("http://ubuntuforums.org/showthread.php?t=1112664") to encrypt all the transactions, particularly the logins.

If you get permission denied errors on /mediashare, make sure the files are readable by the "www-data" user that is running the apache2 process.  (You don't want the HTTP server to have root privileges for security reasons.)  The easiest solution is to make sure all the files can be read by anyone ("chmod -R o+r /home/mike/mediashare").  If the drive is mounted by ntfs or ntfs-3g, you may need to specify the owner and group of the file system manually in the mount options.

What filesystem is on the NAS?  Is it ext3/4 or a Microsoft filesystem like FAT32 or NTFS?  When it's mounted, what does the "mount" command show for this device?

Finally, logs are your friends.  Take a look in /var/log/apache2 and see what shows up in error.log.

---

### Post by darkenedday on 2011-02-20
the mount command says cifs, however i remember reading that the dns-321 from dlink actually uses ext-3 with it's own samba like system. . . found a few articles online said it uses either ext2 or 3, going to try changing from cifs in my mount command to ext2, then 3, and see if it works that way.

turns out that didn't work, however cifs continues to work, i am certain that the NAS uses a linux file system (as it runs it's own stripped down linux OS

error log files gives this message
[Sun Feb 20 12:27:09 2011] [error] [client 192.168.0.101] File does not exist: /var/www/mediashare
i don't know much about this but isn't that the wrong directory?

---

### Post by SeijiSensei on 2011-02-20
Did you add the <Directory> stanza for /mediashare?  Did you restart Apache?  Can you repost the entire virtualhost declaration?  It's easier to read if you put it inside of [noparse]```

```[/noparse] tags.

Also you have a second <Directory /var/www> stanza which is unnecessary.  In fact, I don't know how that interacts with the equivalent stanza above it.

---

### Post by darkenedday on 2011-02-20
alright here's the code, I did put in that stanza like you said to, 

```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
    Alias /mediashare "/home/mike/mediashare"
	<Directory "/home/mike/mediashare">
	  Options Indexes FollowSymLinks MultiViews
          AllowOverride None
          Order allow,deny
          allow from all
	</Directory>
	
</VirtualHost>

```

---

### Post by SeijiSensei on 2011-02-20
Things to try:

1)  Remove the quotation marks from the Alias statement.  I'm not sure they're correct there, even though they're certainly correct in a <Directory> statement.

2)  Replace /var/www as the DocumentRoot with /home/mike/mediashare.  Remove the <Directory /var/www> stanza and remove the Alias that refers to /home/mike/mediashre.  That makes /home/mike/mediashare the default for requests to [http://your.ip.address/](http://your.ip.address/).

```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/mike/mediashare
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>

	<Directory "/home/mike/mediashare">
	  Options Indexes FollowSymLinks MultiViews
          AllowOverride None
          Order allow,deny
          allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
	
</VirtualHost>

```

***This is a last resort***.  If you take this approach, and make your server visible to the public Internet, any HTTP request sent to your public IP will go directly to the NAS.  Without authentication your information will be publicly visible. An Alias provides some "security through obscurity" since random visitors would have to use the /mediashare URL rather than simply [http://your.public.ip.address/](http://your.public.ip.address/).

I'd start by removing those quotation marks first, though.

---

### Post by darkenedday on 2011-02-21
so I attempted removing the quotes to come to another new problem, my browser will not load my ip at all, have been using my local ip to test, usually got the "IT WORKS!!" message from apache...

also as for security didn't you say i could add users and passwords?

---

