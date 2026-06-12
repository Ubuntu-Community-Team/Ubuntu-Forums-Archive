---
title: "Setting Up Squeezeboxserver in Ubuntu"
date: 2011-05-29
forum: Multimedia Software
---

### Post by Andrew F in Australia on 2011-05-29
Hi All,

A quick post to summarise two days of mucking around setting up a Slim Devices Transporter on Ubuntu 11.04 (Narwhal)

(I migrated from windows - permanent, random Blue Screens Of Death and set up a dual-boot system)

I reinstalled Narwhal and set it up in half an hour today following this procedure.

This might be better in beginner help, but it had to be somewhere.

1. Install Ubuntu 11.04 and plug in crossover cable

2.   Install Squeezeboxserver from [http://www.mysqueezebox.com/download](http://www.mysqueezebox.com/download)
2a. You can also install from a terminal server using commands here: [http://www.havetheknowhow.com/Install-the-software/Install-Squeezebox-server.html](http://www.havetheknowhow.com/Install-the-software/Install-Squeezebox-server.html) (a handy site, by the way.)
2b.  Note: It will install MySQL server, don't enter a password.
                 Also, ir will say that the package is untrusted  (full of binary code - install anyway.)

3. Open Synaptic Package Manager Go to: Settings|Repositories|Other Software . Click "Add" and insert the following string. 

deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main

Save the new setting.

4. reboot

5. Set up Transporter - Manually enter IP address 10.0.0.2, subnet mask 255.255.255.000, NO DEFAULT GATEWAY address (000.000.000.000,) DNS server also 000.000.000.000

6. Set up computer as a sever.  eth0 IP address 10.0.0.1, netmask 255.255.255.000, no gateway address (important - if there's a gateway address, the computer will look for an internet connection through the crossover cable and cause problems DAMHIKT.)

7. [IF YOUR MUSIC IS ON A WINDOWS PARTITION OR ON AN EXTERNAL DRIVE YOU MAY NEED TO MOUNT A WINDOWS NTFS PARTITION, DO THIS.]

Go to Ubuntu Software Centre - search for NTFS Configuration Tool and click install. (needs to be installed through terminal window - see instructions in comments on the page.  i

```
To fix this after installing NTFS Configuration Tool
sudo apt-get install ntfs-config
run this in terminal
sudo mkdir -p /etc/hal/fdi/policy
Now run NTFS Configuration Tool.

Tanase Andrei's comments, not mine, but they work perfectly.

See NTFS Configuration tool Comments
```8. Open up firefox or browser window.
8a. Type in 10.0.0.1:9000 into the address bar
8b. SqueezeBox Server window opens up - set music location, then favourites location, then follow prompts to scan music collection. 

All done - worked for me.
{I'm not setting up a mysqueezebox.com account, so have not checked these settings.)

Cheers,

AF

---

### Post by charlesvr on 2011-06-08
Hi.... Was happy to find your instructions. BUT....I did everything up to item 4. After the reboot I updated the repositories but got a warning, saying that it failed to fetch the string I entered in the point 3. I checked; the string is there and check marked. IN item 5 you mention a program called Transporter, but can not find it anyhwre. Maybe due to the failed update? Can you help me out?:confused:

---

### Post by nothingspecial on 2011-06-08
Just install it from their website

[http://www.mysqueezebox.com/download](http://www.mysqueezebox.com/download)

The transporter is one of their players, you can ignore that bit.

---

### Post by charlesvr on 2011-06-08
I did what you said. Here is the result shown on my Terminal:
Can't open /var/log/squeezeboxserver/server.log (Permission denied) at /usr/share/squeezeboxserver/CPAN/Log/Log4perl/Appender/File.pm line 103.
cha@Keres:~$ sudo squeezeboxserver
[sudo] password for cha: 
[11-06-08 23:40:32.1371] main::init (326) Starting Squeezebox Server (v7.5.4, r32171, Thu Apr 14 09:17:01 PDT 2011) perl 5.010001
[11-06-08 23:40:32.1643] main::changeEffectiveUserAndGroup (890) Warning: Squeezebox Server must not be run as root!  Trying user squeezeboxserver instead.
[11-06-08 23:40:32.3151] Slim::Networking::UDP::init (39) FATAL: There is already another copy of the Squeezebox Server running on this machine. (Address already in use)
[11-06-08 23:40:32.3156] Log::Log4perl::Logger::and_die (868) Warning: FATAL: There is already another copy of the Squeezebox Server running on this machine. (Address already in use) at /usr/share/squeezeboxserver/lib/Log/Log4perl/Logger.pm line 900

IF there is another copy no idea where it came from . Sorry
By the way, was you quote a statement or a reprimand?

---

