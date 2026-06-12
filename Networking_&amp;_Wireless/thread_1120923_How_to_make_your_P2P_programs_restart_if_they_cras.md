---
title: "How to make your P2P programs restart if they crash or electricity fails"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by Fernando Negro on 2009-04-09
(Unless you have some sort of old-fashioned type of power button different than most people have nowadays, for this, you obviously need someone who can turn the computer back on, once electricity returns...)


Many of you, who have broadband connections, probably not only use P2P file sharing programs, but also leave your computer on during the night or for days during the week while you're not at home.

And if you use aMule or some other not-so-stable program, you most probably have had the experience of returning back to your computer, after hours or days, only to realize that the program you were running has crashed in the meantime, making all the electricity spent in the partially failed operation worthless.


This small tutorial is for anyone who has a limited, or even sporadic, access to his or her computer, but still wants to use the P2P file sharing networks for long periods of time and stop wasting any more electricity.

Here is what you need to do to solve the problem.


**1**. First of all, make sure your Internet connection restarts by itself if it fails.

- If you have a router, it should probably be already configured to do that on it's on. Make the test of unplugging and plugging back again the line and see what happens. If it doesn't reconnect, you have to configure it to do so by itself.

- If you have a simple ADSL modem that uses the "ppp" protocol, edit your "/etc/ppp/options" file and enable the "persist" option by removing the "#" symbol before it. Also, it might be a good idea to enable the "holdoff" option, the same way, in the same file, and make your modem wait a few seconds before trying to reconnect. For example: "holdoff 2".


**2**. Make sure your P2P programs are configured to try to reconnect if the connection fails. For example, aMule has the option "Reconnect on loss".


**3**. If there's someone else living in your house who can turn the computer back on after a power supply failure occurs, and if you want it to restart downloading and sharing as soon as possible, do the following. If not, jump to step 4.


3.1. If you don't have a router, make your modem connect once the computer boots.

- In other words, if you have a modem that doesn't operate independently from the computer (that doesn't have it's own source of energy) and don't have a boot script installed yet to start the connection during boot, search the Internet for how to do it for your specific modem. For example, for mine the instructions are here: [http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html](http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html).

- Or, if you can't find that information, include the command to start the modem connection in the script described in 3.3. in a second line between "#!/bin/bash" and "sleep x".

> #!/bin/bash
command-to-start-connection
sleep x; first-program &


3.2. Activate the automatic or timed login option, depending on the number of people who use your computer

- Go to "System > Administration > Login Window" and do it in the "Security" window.


3.3. Create a startup script to automatically start your P2P programs once it logs in to your account.

- In a text editor, write, for example:

> #!/bin/bash
sleep 12; amule &
sleep 12; deluge &

Or substitute "amule" and "deluge" by the programs you use, and write a different number of seconds before you want them to start.


**4**. If you created a startup script as described in step 3, add a so-called "daemon" to it, to make it restart a program you use that sometimes crashes. If you don't have a startup script, just create the daemon on it's own.

- For example, if you want your computer to check every minute to see if aMule is running and, if it's not running, restart it, add the following to the script, or create one file with the following text (with a "#!/bin/bash" line first) in a text editor:

> while true; do
  COUNT=`ps -ef | grep -v grep | grep -c amule`
  if [ $COUNT == 0 ]; then
  amule &
  fi
  sleep 1m
done

And if you want it to check for more programs, just repeat the part of the code starting with "COUNT=" and ending with "fi", changing "amule" to the name of the other program(s).

For example, if I wanted my startup script to start amule and deluge two minutes after I log on and keep checking every minute if they have not crashed, I could write something like:

> #!/bin/bash
sleep 2m; amule &
sleep 30; deluge &
sleep 1m
while true; do
  COUNT=`ps -ef | grep -v grep | grep -c amule`
  if [ $COUNT == 0 ]; then
  amule &
  fi
  sleep 30
  COUNT=`ps -ef | grep -v grep | grep -c deluge`
  if [ $COUNT == 0 ]; then
  deluge &
  fi
  sleep 30
done

Adjust the sleep times to the amount you want.

- Save the file you've created with a simple name (for example: "startup"), put it in a chosen directory (for example "~/.local/bin") and make it executable by executing "$ chmod +x 'name-of-the-file'"

If you've created a startup script and not just a daemon you can execute anytime you want, go to "System > Preferences > Sessions" and add the script to the list of programs to be executed at startup.

You might want to pay attention to the time your modem or router usually takes to reconnect after a connection failure and adjust the time before executing the first program in the startup script accordingly to make sure a connection has already been established with your ISP before starting your P2P programs.


That's it. If you have any doubts, ask me. I'm not sure how clear all this is to someone who doesn't know much yet about configuring a GNU/Linux-running computer.


All credit goes to "hwilde" that I met in #ubuntu @ irc.ubuntu.com for teaching me how to write this particular type of daemon.


Happy sharing.

---

