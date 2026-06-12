---
title: "HOWTO: SSH tunnels with secure stored passwords"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by vipseixas on 2009-01-06
I was a happy user of Tunnelier once and I've been trying for months to find a similar Linux native tool without any luck... So I was using Tunnelier under Wine and it worked fairly well but I wanted to use a native tool because Wine emulation of cmd sucks and because I am a purist :)

  What I really wanted was:

- Easy graphical configuration of tunnels (I have to reconfigure them all the time)
- Stored passwords (who gives a s**t to sky-high-security-levels?)

  Now I accomplished this using:

- Gnome SSH Tunnel Manager (gSTM) to easily configure the connections and its tunnels
- Revelation to store the passwords and open the ssh connections
- Self-made scripts (awk and shell) to get the gSTM xml configuration files, convert them into ssh command-lines and then use sshpass to run ssh with the supplied password

  The final result is very simple to use, as you will see. First of all you need to install the apps:

sudo apt-get install gstm revelation sshpass

  Then create these two script in a directory in your path (I put them in ~/bin):

ssh_tunnel.awk
```

#!/usr/bin/awk -f

BEGIN { parseon = 0; tunnel = 0; ssh_params = "" }
/<sshtunnel>/   { parseon = 1 }
/<\/sshtunnel>/ { parseon = 0; ssh_params = host " -p " port " " ssh_params }

!parseon { next }

!tunnel && /<host>/ { host = removeTags($0) }
!tunnel && /<port>/ { port = removeTags($0) }

/<tunnel>/   { tunnel = 1 }
/<\/tunnel>/ { 
	if (tunnel) ssh_params = ssh_params " -" tipo lport ":" rhost ":" rport
	tunnel = 0
}

!tunnel { next }

/<type>/  { (removeTags($0) ~ /local/) ? tipo = "L" : tipo = "R" }
/<host>/  { rhost = removeTags($0) }
/<port1>/ { lport = removeTags($0) }
/<port2>/ { rport = removeTags($0) }

END { print ssh_params }

function removeTags(str) {
	gsub(/[ \t]*/, "", str)
	gsub(/<\/?[a-z0-9]+>/, "", str)

	return str;
}

```

ssh_tunnel.sh
```

#!/bin/bash
export SSHPASS=$3
exec gnome-terminal --tab -x sshpass -e ssh -l $2 `ssh_tunnel.awk $1` >> /dev/null 2>&1

```

  Then do this one-time Revelation config:

[[IMG]http://img261.imageshack.us/img261/9969/configurerevelation1la0.th.png[/IMG]](http://img261.imageshack.us/my.php?image=configurerevelation1la0.png)

  - Use the "generic" type for the tunnels: ssh_tunnel.sh %h %u %p
  - Reconfigure the "shell" type so you can use the stored passwords for regular connections too: gnome-terminal -x sshpass -p %p ssh %(-p %d%) %(-l %u%) %h

  You might be asking why not put the command line that's in the ssh_tunnel.sh file directly in the config. That's because the shell expansions (the command between ``) do not work there (I don't know why).

  Create the tunnels using gSTM:

[[IMG]http://img101.imageshack.us/img101/4112/configuretunnels2jg3.th.png[/IMG]](http://img101.imageshack.us/my.php?image=configuretunnels2jg3.png)

  It is very important that you do not use spaces in the tunnel name, otherwise the script will not work (and I was too lazy the fix it). Don't bother for the login, it will not be used.

  When you configure the tunnels a xml file is created under ~/.gSTM/. You have to find the name of this file (in this example is MyServerTunnels.wOG8aF.gstm) and configure the login/password of the connection in Revelation like this:

[[IMG]http://img201.imageshack.us/img201/2057/configurerevelation2zy8.th.png[/IMG]](http://img201.imageshack.us/my.php?image=configurerevelation2zy8.png)

  That's it! Now you can open the tunnels at the Revelation main window by double-clicking the entry or selecting "go to" from the local menu, or using the fine Revelation Gnome Applet. Every time you change the tunnels config using gSTM it will be automagically used by your Revelation entry.

  You can hack this a little to achieve some different behaviors, like putting the -Nn option in ssh to not run a shell etc.

Hope this will be useful!

[]s!

Vinicius Seixas.

---

