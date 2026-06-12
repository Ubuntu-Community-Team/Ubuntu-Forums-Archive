---
title: "Frontend GUI won't start"
date: 2011-06-18
forum: Mythbuntu
---

### Post by timlash on 2011-06-18
I'm at my wit's end, which is often not far from my wit's beginning.  For the last week I've been working to build a Mythbuntu 10.10 split system.  This is my first foray into MythTV.  I'm using two new AMD64 systems with no other OS on either machine.

The backend build seemed to go smooth, and I think I've correctly configured and bound my video capture card for my local over-the-air broadcast channels.  My backend logs can be found here:

[http://pastebin.com/eRxeyUEF](http://pastebin.com/eRxeyUEF)

I'm currently stuck without a MythTV GUI on my frontend.  Every time I click on 

Applications >> Multimedia >> MythTV Frontend

I get no response.  Otherwise the frontend system seems to be working fine and it reports success when connecting to the backend MySQL DB.  My frontend logs can be found here:

[http://pastebin.com/0Bzts4VM](http://pastebin.com/0Bzts4VM)

I can see many warning and error messages in these logs, but I'm not sure on how best to proceed in resolving them to get the MythTV frontend GUI to work.

Any guidance would be greatly appreciated!

Cheers,

Tim

---

### Post by timlash on 2011-06-18
Not very much progress, but I've made another examination of my logs and highlighted some findings.

_Backend_

1) fixed compiz error with -noxdamage switch on my x11vnc command
2) ignored NTP error - further boot process resolves
3) ignored plymouth error, no encryption in use
4) ignored HEST (Hardware Error Source Table) error, I'll check BIOS later

5) Should I be concerned here, and is there an alternative that I should consider?
Jun 18 20:20:03 fatman kernel: [    2.671843] Linux media interface: v0.10
Jun 18 20:20:03 fatman kernel: [    2.676661] Linux video capture interface: v2.00
Jun 18 20:20:03 fatman kernel: [    2.676664] WARNING: You are using an experimental version of the media stack.
Jun 18 20:20:03 fatman kernel: [    2.676664]   As the driver is backported to an older kernel, it doesn't offer
Jun 18 20:20:03 fatman kernel: [    2.676665]   enough quality for its usage in production.
Jun 18 20:20:03 fatman kernel: [    2.676666]   Use it with care.


6) Tuner Card initialization looks okay.  Agree?
Jun 18 18:54:19 fatman kernel: [   14.350826] saa7164[0]: Hauppauge eeprom: model=88061
Jun 18 18:54:19 fatman kernel: [   14.680821] tda18271 1-0060: creating new instance
Jun 18 18:54:19 fatman kernel: [   14.685222] TDA18271HD/C2 detected @ 1-0060
Jun 18 18:54:20 fatman kernel: [   15.024854] DVB: registering new adapter (saa7164)
Jun 18 18:54:20 fatman kernel: [   15.024857] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
Jun 18 18:54:20 fatman kernel: [   15.314324] tda18271 2-0060: creating new instance
Jun 18 18:54:20 fatman kernel: [   15.318539] TDA18271HD/C2 detected @ 2-0060
Jun 18 18:54:20 fatman kernel: [   15.664726] tda18271: performing RF tracking filter calibration
Jun 18 18:54:23 fatman kernel: [   18.358175] tda18271: RF tracking filter calibration complete
Jun 18 18:54:23 fatman kernel: [   18.358643] DVB: registering new adapter (saa7164)
Jun 18 18:54:23 fatman kernel: [   18.358646] DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
Jun 18 18:54:23 fatman kernel: [   18.358870] saa7164[0]: registered device video0 [mpeg]
Jun 18 18:54:23 fatman kernel: [   18.589536] saa7164[0]: registered device video1 [mpeg]
Jun 18 18:54:23 fatman kernel: [   18.800410] saa7164[0]: registered device vbi0 [vbi]
Jun 18 18:54:23 fatman kernel: [   18.800428] saa7164[0]: registered device vbi1 [vbi]

7) This doesn't look good.  Anyway to know the unknown here?
=== MythtV Backend Log ===
2011-06-18 18:54:50.700 MainServer, Warning: Unknown socket closing MythSocket(0xa49180)
2011-06-18 18:54:52.690 MainServer, Warning: Unknown socket closing MythSocket(0xa6c1d0)


_Frontend_

1) Removed all frontend plugins

2) It looks like the frontend is connecting to the MySQL backend DB
=== MythtV Frontend Log ===
Starting mythfrontend.real..
2011-06-18 18:54:52.238 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org]("http://www.mythtv.org")
2011-06-18 18:54:52.239 Using runtime prefix = /usr
2011-06-18 18:54:52.239 Using configuration directory = /home/timlash/.mythtv
2011-06-18 18:54:52.853 Empty LocalHostName.
2011-06-18 18:54:52.853 Using localhost value of littleboy
2011-06-18 18:54:52.853 Testing network connectivity to '192.168.1.101'
2011-06-18 18:54:52.859 New DB connection, total: 1

The frontend GUI still does not launch.

Am I way off base here?  Is there some surefire MythTV tutorial somewhere that I've skipped?

Thanks for reading,

Tim

---

### Post by timlash on 2011-06-19
Is it possible to start MythTV frontend via CLI?  If so which command would launch MythTV frontend.  Perhaps that would reveal errors messages that could help.

More generally, is there a way to determine the command and/or options behind any item in the Applications menus?

Thanks,

Tim

---

### Post by tgm4883 on 2011-06-20
> **timlash said:**
> Is it possible to start MythTV frontend via CLI?  If so which command would launch MythTV frontend.  Perhaps that would reveal errors messages that could help.

More generally, is there a way to determine the command and/or options behind any item in the Applications menus?

Thanks,

Tim

mythfrontend

---

### Post by ktmom on 2011-06-20
Yes, you can start from the CLI.  It should be as simple as typing "mythfrontend".  Every bit of logging output will go to the screen.  I suspect you have already found the frontend log in /var/log/mythtv/ but if you want to define the logfile elswhere use: "mythfrontend -l file.log"

Many log entries look like errors when they are not.  For example, you were seeing;

> 2011-06-18 18:54:50.700 MainServer, Warning: Unknown socket closing MythSocket(0xa49180)

If I grep my backend log, I get many similar lines.  I suspect that your problem is on the frontend system.   When you start the frontend, did you ever get booted into the setup window?  There you'll be asked for things like how to connect to the backend.  If so, did you enter the backend's IP address for the Hostname in the database server configuration?  On remote frontends, the Hostname should never be localhost.

Can you ping the backend from the frontend?  Have you looked at this [mythtv link]("http://www.mythtv.org/wiki/MythFrontend")?

On another note:  

> More generally, is there a way to determine the command and/or options behind any item in the Applications menus?

Practically, the way I do it is to right click, add launcher to the desktop then right click the item on the desktop and in the properties Command box is the command that will work on a command line.  I'm sure there is a "right way" but it works.  I don't know if that works on Xfce, but it does work on gnome.

---

### Post by klc5555 on 2011-06-21
Make sure MySQL on the backend has been set (in the Mythbuntu control center) to allow remote connections. Make sure also that the PIN in the setup has been set to 0000 to allow connections from any frontend.

From the log it looks like the frontend successfully tests the connection, but doesn't actually make the connection. If it did, you'd immediately see it having made "New DB connection, total: 2" and eventually, right before the frontend theme loads, a 3rd connection.

---

### Post by timlash on 2011-06-22
Thanks tgm, ktmom and klc for your replies.  They were each helpful.  Unfortunately I'm still stuck.

Using the fontend CLI command I was able to start mythfrontend with the verbose option and I captured those messages here:

[http://pastebin.com/zpfyY0Zn](http://pastebin.com/zpfyY0Zn)

Some of the questionable highlights were:

           (old)Settings::ReadSettings(settings.txt) - No such file
           (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - No such file
           (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file

Defaults used instead?

I had a nonzero PIN on the backend but changed it to 0000 as recommended.  Then I tried changing the frontend PIN to 0000.  However, now when I test frontend remote connectivity in the MySQL tab of Mythbuntu Control Center, that whole program hangs.  That seems like a step backward.

Lastly, I also did some poking around, and found the following two config files with different MySQL passwords for the mythtv user.  That doesn't seem right.

/etc/mythtv/config.xml contained:

<Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
<!--
Set the <LocalHostName> hostname override below only if you want to use
something other than the machine's real hostname for identifying settings
in the database.  This is useful if your hostname changes often, as
otherwise you'll need to reconfigure mythtv every time.

NO TWO HOSTS MAY USE THE SAME VALUE
-->
        <DBHostName>localhost</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>pwd-one</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>6543</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>


While /home/timlash/config.xml looks like this:

<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>c5d794ae-1961-4a80-9873-143690747221</MediaRenderer>
    </UDN>
    <MythFrontend>
      <DefaultBackend>
        <USN/>
        <SecurityPin>0000</SecurityPin>
        <DBHostName>192.168.1.101</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>pwd-two</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>6543</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

The only idea I have left is to try and re-install the frontend from scratch for the n-th time.  Please don't ask me to supply a value for n.

Any further suggestions?  Thanks.

---

### Post by tgm4883 on 2011-06-22
Have you ever tried to compile mythtv rather than use the Ubuntu/Mythbuntu provided packages?

---

### Post by nickrout on 2011-06-23
so which one is the correct password?

---

### Post by timlash on 2011-06-24
tgm, recompiling seems like an extreme step.  Does doing so offer an inherent benefit?

nickrout, good question!  I'll be sure to test them.

---

### Post by tgm4883 on 2011-06-24
> **timlash said:**
> tgm, recompiling seems like an extreme step.  Does doing so offer an inherent benefit?

nickrout, good question!  I'll be sure to test them.

I wasn't telling you to recompile, I was asking if you had previously done so.

---

### Post by nickrout on 2011-06-24
One thing I noticed from your logs is that frontend seems to be trying to connect to the backend database as the root user, not as mythtv. This is wrong. How it got like that, heaven knows.

---

### Post by jacksaff on 2012-04-15
> **timlash said:**
> 

While /home/timlash/config.xml looks like this:

<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>c5d794ae-1961-4a80-9873-143690747221</MediaRenderer>
    </UDN>
    <MythFrontend>
      <DefaultBackend>
        <USN/>
        <SecurityPin>0000</SecurityPin>
        <DBHostName>192.168.1.101</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>pwd-two</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>6543</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>



<DBPort> refers to the port for mysql on the backend server. It almost certainly isn't 6543! Putting 0 there fixed this for me as it just then uses the default mysql port.

After much hair pulling over the same problem I thought I would resurrect this thread as I came across it during my searching and others may too...

---

