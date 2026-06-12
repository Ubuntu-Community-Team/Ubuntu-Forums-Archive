---
title: "Automatically Mount Itouch on Discovery"
date: 2009-02-10
forum: Multimedia Software
---

### Post by mastermindg on 2009-02-10
My configuration:

Hardy 8.04, 2.6.24-21-generic
Static IP on local
Static IP on iTouch
OpenSSH on both devices

I've configured my iTouch to use sshfs (fuse). I can connect fine and have gotten Amarok working with it. Everything is great in this respect.

What I would like is to be able to have done is the ability to mount the filesystem whenever it is available. Obviously I'm going to go outside of the range of my router once and a while, so I'd like for my system to detect when the iTouch is back. 

One issue that I'm having is that passwordless login via OpenSSH isn't working. I've followed the procedures and verified that id_rsa.pub matches authorized_keys, and set permissions on remote directory/file. I've verified that RSAAuthentication is set on sshd. Still my iTouch is asking for my password.

I suppose I could get around this, though. But how?

---

### Post by mastermindg on 2009-02-10
Well, I figured it out how to do it

 :guitar:

Installed pexpect, a python module that connects to expect.

```

#!/usr/bin/python
import pexpect
import time

command = "sshfs root@YOURIP:/var/mobile/Media /media/itouch/ -o reconnect"

def start_sshfs():
    	try:
	    sshfs = pexpect.spawn(command)
	    sshfs.expect("root@YOURIP's password: ")
	    time.sleep (0.1)
	    sshfs.sendline ("YOURPASSWORD")
	    time.sleep (10)
	    sshfs.expect (pexpect.EOF)

	except Exception, e:
		print str(e)

def main ():
	start_sshfs()

if __name__ == '__main__':
	main ()

```

Spacing is obviously an issue with python, so copy/paste like it is here or you'll get an IndentationError message. Just replace YOURIP with your ip and if you changed the default password for root, change it under YOURPASSWORD. You can login under other users as well.

The reconnect option allows the connection to be more resilient. I've got Amarok setup to run this script on connect.

---

