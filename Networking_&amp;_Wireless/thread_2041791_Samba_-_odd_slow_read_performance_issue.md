---
title: "Samba - odd slow read performance issue"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by xtensik on 2012-08-13
Hello there, a mildly experienced (know how to use the CLI/Terminal, edit config files and tweak easily accessible things) Linux user here.

I have used an AMD E350 Fusion Mini-ITX board to build a HTPC/Fileserver for easy access of media, mostly movies and tv-shows, running Lubuntu 12.04 with XBMC (the XBMC-XvBA variant to be precise). I have been using a [guide]("http://youresuchageek.blogspot.fr/2012/06/xbmc-install-and-config-howto-for-linux.html") to install and configure all of the needed software for that purpose.

Right now I have set up a basic Samba install with an unsecured global guest share for easy uploading and access to my media library from Windows clients (exclusively Windows 7 x64, one client upgraded to SP1) on a closed, wired 1Gbps network. The share is set up on a LVM stripe connecting two WD20EARS 2TB harddrives.

The problem I'm seeing is Samba being unable to maintain fast (>60MB/s) read speeds, while writes are universally fast and consistent. This is a known problem and have been remedied in the past with adding opcodes to smb.conf... but here's the fun part:

It's not consistent.

I have been restarting the service as part of debugging my problem, and have noticed that on some restarts, Samba behaves properly, with read speeds consistent with the overall network speed. Earlier on I thought it was a result of tweaking and left it to work, but recently I had to reboot the server a couple of times and the problem comes back. I have now determined that Samba behaves erratically and there is no visible pattern to whether it behaves as it should or not.

I have been trying to determine whether the problem was with the drives, the LVM share, the CPU/RAM bottlenecking the board, the network gear or the network itself and i have no clues whatsoever - local readwrite tests show absolutely no problems with accessing the data and the network works as intended. Stresstests on a "good" service start are all green, and XBMC playing a 1080p h264 file has no impact other than stressing the CPU and reading from the same drive from which the file was copied over the network. That leaves me with some potential Samba issue with which neither my current knowledge nor Google could help me. I have tried tweaking my smb.conf on my own, but other than a few optimization tweaks, "bad" service starts still occur.

Here is my current smb.conf. It is a giant mess right now owing to different methods of trying to solve my problem:
```
[global]
        ;General server settings
        netbios name = SOULFORGE
        server string = Domowy serwer plikow
        workgroup = WORKGROUP
        domain master = yes
        local master = yes
        preferred master = yes
        load printers = no
        printing = bsd
        printcap name = /dev/null
        disable spoolss = yes
        announce version = 5.0
        passdb backend = tdbsam
        security = share
        guest account = nobody
        null passwords = true
        name resolve order = bcast host lmhosts wins
        wins support = yes
        interfaces = lo, eth0
        bind interfaces only = true
        syslog = 1
        syslog only = yes
        log level = 1
        strict locking = no
        strict sync = no
        sync always = no
        large readwrite = no
        min receivefile size = 16384
        use sendfile = true
        aio read size = 16384
        aio write size = 16384
        read raw = yes
        write raw = yes
        kernel oplocks = yes
        max xmit = 65535
        dead time = 15
        getwd cache = yes

[Dane]
        path = /mnt/dysk
        public = yes
        browseable = yes
        guest only = yes
        writable = yes
        case sensitive = True
        oplocks = yes
        create mask = 0777
        directory mask = 0777

```

---

### Post by xtensik on 2012-08-14
Just reinstalled a clean Ubuntu Minimal on the system with currently nothing other than Samba on it - no window managers, no servers, no XBMC, no nothing. The weird behaviour is still present, so I can probably rule out inadvertant meddling with my setup.

---

### Post by xtensik on 2012-08-14
Some more testing!

Installed minimal stable Debian Squeeze onto the hardware with nothing but Samba (3.5.6) and what do you know - it is loads faster than the one bundled with Ubuntu 12.04 (3.6.3) for some reason. I used a very, very basic smb.conf for the initial testing (already fast and stable by itself) and tweaked it around a bit - now I have consistent, very fast reads and writes every service start, with maybe realtime access (skipping through huge videos) not as fast as i'd have hoped to have with a 1Gpbs network - but it works without fail and doesn't cause headaches every time i wish to download my media.

Here is my current smb.conf:
```
[global]
   workgroup = WORKGROUP
   server string = Domowy Serwer Plikow
   wins support = no
   dns proxy = no
   name resolve order = lmhosts host wins bcast

   interfaces = 127.0.0.0/8 eth0
   bind interfaces only = yes

   log file = /var/log/samba/log.%m
   max log size = 1000

   panic action = /usr/share/samba/panic-action %d

   security = share

#MODS

   strict locking = no
   strict sync = no
   sync always = no
#OH YOU   min receivefile size = 16384
#OH YOU   use sendfile = true
#OH YOU   aio read size = 16384
#OH YOU   aio write size = 16384
   read raw = yes
   write raw = yes
   kernel oplocks = yes
#OH YOU   max xmit = 65535
   dead time = 15
   getwd cache = yes

[Dane]
   public = yes
   browsable = yes
   read only = no
   writeable = yes
   create mask = 0777
   directory mask = 0777
   guest ok = yes
   guest only = yes
   path = /mnt/dysk
```The options commented out and marked with OH YOU were causing significant slowdowns, probably due to buffer scale mismatch. Having not enough time to properly find them myself, for now they'll have to stay that way.

Sendfile is a very interesting option - it caused exactly the same behaviour that I noticed with the Ubuntu-bundled Samba, that is on some service starts everything was fast and without problems, but other times it significantly lagged (<10MB/s, not the expected >60MB/s) with reads.

Right now I am considering either trying to go back to my first, mostly complete setup and forcing Sendfile off (not sure if it is enabled by default) to see if it alleviates my problem, or building up my whole setup from Debian. I am not yet marking this as solved, but I am almost sure that Samba itself is the problem here.

---

### Post by xtensik on 2012-08-14
Well, after restoring an image with the mostly complete Lubuntu 12.04 install, i have checked whether forcing Use Sendfile off helped.

It didn't.

Right now I'm compiling samba 3.5.17 by hand on the target machine, to check if maybe the 3.6 branch is problematic. If that doesn't work, I'll compile 3.5.6 and check. If that also will not work... well, Debian it is i suppose.

---

### Post by xtensik on 2012-08-14
Welp, compiling Samba 3.5.17 on the Lubuntu install didn't work - it still exhibits this behaviour. I'm not sure if I want to try compiling 3.5.6 now - it seems that Ubuntu is the problem somehow. For now, I'm giving up so to speak and will expand upon the Debian install.

---

### Post by xtensik on 2012-08-15
After deciding to take one more stab at it, i got it working on my first (Lubuntu 12.04) install \o/ .

The offenders were raw read/write, large readwrite and use sendfile - those options were causing problems with Samba, but the final touch was getting max xmit just right - for some reason my router does not accept standard (big) SMB structures properly and even a default Win2k size transmission was giving it problems. I tuned it just right to achieve maximum performance vs. maximum throughput.

Here is the final, not cleaned up yet config file with assorted speed tweaks, some of which might not work for your setup and/or slow it down. Keep in mind that this should not be treated as a one-stop solution, but this is what worked for me.

Marking this one as solved.

```
[global]
   workgroup = WORKGROUP
   server string = Domowy Serwer Plikow
   wins support = no
   dns proxy = no

   interfaces = 127.0.0.0/8 eth0

   log file = /var/log/samba/log.%m
   max log size = 1000

   panic action = /usr/share/samba/panic-action %d

   security = share

#MODS

   disable netbios = yes
   disable spoolss = yes
   domain logons = no
   max protocol = SMB2
   socket options = TCP_NODELAY IPTOS_LOWDELAY
   large readwrite = no
   strict locking = no
   strict sync = no
   sync always = no
#    min receivefile size = 16384
#   use sendfile = true
#   aio read size = 16384
#   aio write size = 16384
#   read raw = yes
#   write raw = yes
#   kernel oplocks = no
    max xmit = 12288
   dead time = 15
   getwd cache = yes

    domain master = yes
    local master = yes
    preferred master = yes

[Dane]
   public = yes
   browsable = yes
   read only = no
   writeable = yes
   create mask = 0777
   directory mask = 0777
#   level2 oplocks = yes
#   oplocks = no
   guest ok = yes
   guest only = yes
   path = /mnt/dysk
```

---

