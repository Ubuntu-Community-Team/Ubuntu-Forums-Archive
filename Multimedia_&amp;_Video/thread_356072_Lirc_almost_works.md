---
title: "Lirc almost works"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by Shawn Dineley on 2007-02-08
Hello

     I've been trying to get Lirc to work for the last couple the days. I have a IRA-3 receiver. Which from what I understand using something called irman.
And a Tivo series 2 remote.So I installed libirman-0.4.3 and got it configured and installed. But in when I configure all the buttons for the remote. And then go back to test them. Using the command "test_name" the receivers LED comes on. But I don't get any commands on the screen? 
    And I get the same problem with Lirc. I ran the record command,and did all that. But then I go back to test them. Start Lirc and run irw. Press some buttons, and nothing happens on the screen. As before the status LED comes on and blinks when I hit the buttons. 

     So what I'm I forgetting?? Please Help

P.S Oh ya I running ubuntu 6.10

---

### Post by Shawn Dineley on 2007-02-08
Bump

---

### Post by racmar on 2007-06-21
I have the same device, I got mine to work using lirc.  Here is my /etc/lirc/hardware.conf file:


```

# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
#LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
#LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
#DRIVER="irman"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
#DEVICE="/dev/ttyS0"
#MODULES=""

# Default configuration files for your hardware if any
#LIRCD_CONF="/etc/lirc/lircd.conf"
#LIRCMD_CONF=""


DRIVER="irman"
DEVICE="/dev/ttyS0"
#LIRCD_CONF="/etc/lirc/lircd.conf"
MODULES="UNCONFIGURED"
LIRCD_CONF="UNCONFIGURED"
LIRCMD_CONF="UNCONFIGURED"

```

---

### Post by bignickel on 2007-07-05
I've been having little luck with my ira-3.  I used the hardware.conf above, and that actually allows me to start lirc, which I was unable to do before.  Then, when I run irw the red light on the ira-3 comes on, and when I press button the light flickers, but nothing comes up on the screen.

I made a lircd.conf file using the following command:
```
# sudo irrecord --driver=irman --device=/dev/ttyS0 \
	/etc/lirc/lircd.conf
```

and that seems to work fine.  But I still can't get anything when lirc starts.  Any suggestions?

---

### Post by racmar on 2007-07-05
I have been unable to get irman working with the default lirc in feisty.  If you are using feisty: [check my post here]("http://ubuntuforums.org/showthread.php?t=394045&highlight=irman")

I've bought about 4 ira-3 devices, and I actually received a bad one.  It had similiar symptoms, but I loaded the official ira-3 software from their website on a windows machine.  I found out it was non-functional, so  I called them and did an RMA.  They were very nice and easy to work with.

---

### Post by bignickel on 2007-07-05
I downgraded to the Edgy version of lirc, and the same thing happens.  I don't think the unit is broken though, because irrecord still works, and if I cat /dev/ttyS0 I can see the button presses.  But when I start lirc, I still get nothing from irw.

Did you just install the old version of lirc with your custom hardware.conf and it worked?  There must be something I'm missing somewhere.

---

### Post by racmar on 2007-07-05
Pretty much, that's what I did.  I redirected the irrecord command to a different file, then just copied the file to lircd.conf, to save a copy for later.

What does the output of the following show?  I'm interested in the output around the irw and first keypress.
```
cat /var/log/daemon.log | grep -i lircd
```

Also, what does setserial show?
```
setserial /dev/ttyS0
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4

```

---

### Post by bignickel on 2007-07-05
Aha, that helped.  When I looked at the daemon.log, it said:

```
Jul  5 13:24:41 server lircd-0.8.0[6442]: error in configfile line 27:
Jul  5 13:24:41 server lircd-0.8.0[6442]: unknown definiton or too few arguments: "toggle_bit_mask 0x0"
Jul  5 13:24:41 server lircd-0.8.0[6442]: reading of config file failed

```

Line 27 in lircd.conf was:

```
toggle_bit_mask 0x0
```

so I commented that out and now I'm getting a response from irw.  Thanks for the help!

---

### Post by racmar on 2007-07-05
Great!  Glad I could help.  I was wondering if you might try the newer feisty lirc and see if your setup will still work.  I'd appreciate it if you would try.

---

### Post by bignickel on 2007-07-05
I will try that, but I have one more question.  I created my .lircrc file, but now I'm wondering how the applications know to activate the receiver.  I have my .lircrc set up with some commands for mplayer and mythtv, but the red light isn't on the receiver, so I guess it's not ready to accept commands.  How do I activate it?

---

### Post by racmar on 2007-07-05
that depends on the application.  In my case, mythtv is setup as a standard linux user account.  Thus, my setup is like this:

/home/mythtv/.lircrc
```
begin
        prog = mythtv
        button = up
        config = Up
        repeat = 1
end
begin
        prog = mythtv
        button = down
        config = Down
        repeat = 1
end
begin
        prog = mythtv
        button = left
        config = Left
        repeat = 1
end
begin
        prog = mythtv
        button = right
        config = Right
        repeat = 1
end
begin
        prog = mythtv
        button = ok
        config = Return
end
begin
        prog = mythtv
        button = exit
        config = Esc
end
begin
        prog = mythtv
        button = info
        config = I
end
begin
        prog = mythtv
        button = skip_fwd
        config = End
end
begin
        prog = mythtv
        button = skip_rev
        config = Home
end
begin
        prog = mythtv
        button = menu
        config = M
end
begin
        prog = mythtv
        button = record
        config = R
end
begin
        prog = mythtv
        button = pause
        config = P
end
begin
        prog = mythtv
        button = cc
        config = T
end
begin
        prog = mythtv
        button = fwd
        config = U
end
begin
        prog = mythtv
        button = rev
        config = J
end
begin
        prog = mythtv
        button = play
        config = A
end
begin
        prog = mythtv
        button = mode
        config = F8
end

```


and then I had to setup a symbolic link like this:
```
ln -s /home/mythtv/.mythtv/lircrc /home/mythtv/.lircrc

```


And remember to restart mythfrontend

---

### Post by bignickel on 2007-07-05
My .lircrc looks almost identical.  At what point should the red light go on?  When the myth frontend loads?  Because right now it only lights when I run irw.

---

### Post by racmar on 2007-07-05
did you create the symlink?  Because the red light should come on when myth-frontend loads, almost immediatly.  you will see in the /var/log/daemon.log file a new client has been added...

---

### Post by bignickel on 2007-07-05
Is this normal?

```
Jul  5 16:15:40 server lircd-0.8.0[4660]: accepted new client on /dev/lircd
Jul  5 16:15:41 server lircd-0.8.0[4660]: removed client
```

It looks like it's getting the client when I start myth, and immediately releasing it.

UPDATE:  it works fine for mplayer, so there's just something with myth

UPDATE2: I'm an idiot.  I thought it was DOTlircrc in the .mythtv folder, and now I see it's just lircrc (with no dot).  Thanks a lot for your help, I'm really happy to have it working!

---

### Post by Skidd on 2007-07-21
Hi Guys.
Sorry to re-open an old theread there, but I seem to be having the exact same problem, but not the same solution.

irrecord works perfectly, and generates an lircd.conf file successfully.
Then, when I start lirc, and try irw, I get nothing.

I have had the same remote and irman device working before on this same computer.  I used to be running Gentoo as my HTPC, and switched to Ubuntu recently.  lirc and my remote worked fine when Gentoo was installed.  I even tried the exact copy of the lircd.conf file from my Gentoo install.

When I look at the contents of daemon.log.. It shows now error messages.  It simply shows irw connecting and disconnecting.

Just for the heck of it, I even tried downloading and compiling lircd from the source.  It acts the exact same way.

Here is a shortended (for testing) version of my lircd.conf file.

```
begin remote

  name  lircd.conf
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   48
  pre_data       0xFFFF00076E3E
  gap          207952
  min_repeat      4
  toggle_bit_mask 0x0

      begin codes
          up                       0x0F8F
          down                     0xCF4F
          left                     0x6FEF
          right                    0xAF2F
          ok                       0x1898
      end codes

end remote

```


Here is my hardware.conf
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=false

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="irman"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/ttyS0"
MODULES="UNCONFIGURED"

# Default configuration files for your hardware if any
LIRCD_CONF="UNCONFIGURED"
LIRCMD_CONF="UNCONFIGURED"

```

and if I ps for lircd, here is what is shoing to be running.
```
root     25452     1  0 08:43 ?        00:00:00 /usr/sbin/lircd --driver=irman --device=/dev/ttyS0

```

Anybody have any idea where to look for this problem?  Is this an irman issue?  Should I just breakdown and try a different type of hardware?   I hate to since it's been working perfectly for almost 4 years now.

Shane.

---

### Post by racmar on 2007-07-21
What does this show?
```
dpkg -l lirc
```
It should look like this:  ( notice the version number is 0.8.0-5ubuntu1 )
```
ii  lirc                                  0.8.0-5ubuntu1                        Linux Infra-red Remote Control support
```



If you are using Feisty, the newest lirc does NOT work.  You can downgrade lirc by doing this:

Edit /etc/apt/sources.list
```
sudo nano /etc/apt/sources.list
```

And add this line:
```
deb http://archive.ubuntu.com/ubuntu edgy universe
```

Then, update and force the older version:
```
sudo apt-get update
sudo apt-get install lirc=0.8.0-5ubuntu1
```



If you do not want future upgrades to overwrite your lirc, you can accomplish this by "pinning":

You should create a file called /etc/apt/preferences 
```
sudo nano /etc/apt/preferences
```

and it should contain the following:
```
Package: *
Pin: release a=feisty
Pin-Priority: 650

Package: lirc
Pin: version 0.8.0*
Pin-Priority: 1001

```

---

### Post by Skidd on 2007-07-21
Woh.. That was way too easy.  It works perfectly now!  Thanks!

---

### Post by bignickel on 2008-03-15
Well, after everything running fine for several months, my ira-3/lirc combination has stopped working.  I didn't upgrade anything, I was just using it one minute and the next minute it didn't work.  I booted up in Windows and everything works, so it's not the unit or the remote.  If I cat /dev/ttyS0 the light comes on, and I can see one button press (the TV/Video button for some reason) but no others.  Every button press makes the LED flicker a little bit (as usual), but nothing comes through.  Any ideas?

---

### Post by racmar on 2008-03-15
what do you get when you run the following?

```
cat /var/log/daemon.log | grep -i lirc
```

---

### Post by bignickel on 2008-03-15
The output of daemon,log after restarting lirc and opening up mplayer is 
```

Mar 15 16:45:54 server lircd-0.8.0[18377]: lircd(userspace) ready
Mar 15 16:45:57 server lircd-0.8.0[18377]: accepted new client on /dev/lircd
Mar 15 16:46:05 server lircd-0.8.0[18377]: removed client
Mar 15 16:47:09 server lircd-0.8.0[18377]: accepted new client on /dev/lircd
Mar 15 16:47:10 server lircd-0.8.0[18377]: removed client
```

I tried doing another irrecord, and it works fine but when I run irw nothing is coming up.  Maybe I should try upgrading lirc.

---

### Post by racmar on 2008-03-15
You can always try upgrading, the lirc problems may have been fixed by now.  I had a similar problem and it was a bad / loose cable.  But since you got it working in windows, i'm guessing your cable is fine. 

I recently stopped using lirc, and bought a firefly mini.  It acts as an actual keyboard, so no more lirc problems!  I do still have one frontend machine using lirc, but it's been rock solid.

---

