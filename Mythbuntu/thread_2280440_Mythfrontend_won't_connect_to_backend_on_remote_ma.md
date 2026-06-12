---
title: "Mythfrontend won't connect to backend on remote machine"
date: 2015-05-30
forum: Mythbuntu
---

### Post by bilkay on 2015-05-30
I'm trying to get mythfrontend running on a laptop (ubuntu 12.04) connecting to a PC (mythbuntu 14.04) running the backend (everything works fine there). The backend version is 0.27 so I had to:

```

sudo add-apt-repository ppa:mythbuntu/0.27
sudo apt-get updat

```

I can  connect to the database with mysql:

```

mysql -h Jupiter -u mythtv -D mythconverg -p
password:

```

But when I try to run mythfront.real, I get this repeating message:

```

2015-05-30 15:38:04.111624 I  MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2015-05-30 15:38:04.112494 E  MythSocket(9939670:-1): Failed to connect to (127.0.0.1:6543) Connection refused
2015-05-30 15:38:04.114759 E  Connection to master server timed out.
            Either the server is down or the master server settings
            in mythtv-settings does not contain the proper IP address


```

All the database settings are correct. I tried both the Hostname server name (Jupiter) and its IP address with the same result.

Poring through a lot of threads trying to find an answer, I see several references to running mythtv-setup. It's not installed since I didn't install the backend on the laptop. Do I need to? Or is there something else I'm missing?

---

### Post by bilkay on 2015-05-30
I think I found the answer to my first question and installed the backend on the the laptop. But it still won't connect to the master backend on the PC. Now I get the following when running mythfrontend.real:

```

2015-05-30 17:14:26.062726 I  MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
2015-05-30 17:14:26.065408 E  MythSocket(ffffffffb4033340:-1): Failed to connect to (192.168.1.104:6543) Connection refused
2015-05-30 17:14:26.067770 E  Connection to master server timed out.
            Either the server is down or the master server settings
            in mythtv-settings does not contain the proper IP address

```
The master backend is running, the IP address is correct, and there's no firewall between the laptop and the PC.

I thought it might be a PIN problem and checked the master setup - it was set to blank. I changed it to 0000 but I still can't connect.

---

### Post by blm-ubunet on 2015-05-30
You don't need backend installed unless this is to run as slave backend.
But it should not cause any harm & is small (relatively).
The slave is determined by use of mixed IP addresses in mythtv-setup.

Is this "192.168.1.104" the master backend IP address.

Does this work in browser (on remote FE)?
```
http://Jupiter:6544/Myth/wsdl
```

The frontend uses the contents of config.xml file to find host & IP addresses etc.
It looks in multiple locations for this file:-
1. /home/<user>/.mythtv/config.xml
2. /etc/mythtv/config.xml

This can be confused by how you launch myth programs (i.e. as which user)..
For example the backend should always be started as "mythtv".

There has been recent bugs in the config.xml IP vs hostname parsing etc..
What is the contents of "/home/<user>/.mythtv/config.xml" ?

The other problem could be version mismatches which you have tried to mitigate by using same mythbuntu versions..

---

### Post by bilkay on 2015-05-31
> **blm-ubunet said:**
> You don't need backend installed unless this is to run as slave backend.
But it should not cause any harm & is small (relatively).
The slave is determined by use of mixed IP addresses in mythtv-setup.

Is this "192.168.1.104" the master backend IP address.
Yes. (And thanks for responding!)
> **blm-ubunet said:**
> Does this work in browser (on remote FE)?
```
http://Jupiter:6544/Myth/wsdl
```

No. It doesn't work with the IP address either.
> **blm-ubunet said:**
> The frontend uses the contents of config.xml file to find host & IP addresses etc.
It looks in multiple locations for this file:-
1. /home/<user>/.mythtv/config.xml
2. /etc/mythtv/config.xml

This can be confused by how you launch myth programs (i.e. as which user)..
For example the backend should always be started as "mythtv".

There has been recent bugs in the config.xml IP vs hostname parsing etc..
What is the contents of "/home/<user>/.mythtv/config.xml" ?
This is from ~/.mythtv/config.xml 
```
<Configuration
  <UPnP>
    <UDN>
      <MediaRenderer>29809db2-7a99-463c-b0ce-c1c2151218d4</MediaRenderer>
    </UDN>
  </UPnP>
  <LocalHostName>my-unique-identifier-goes-here</LocalHostName>
  <Database>
    <PingHost>1</PingHost>
    <Host>Jupiter</Host>
    <UserName>mythtv</UserName>
    <Password>mythtv</Password>
    <DatabaseName>mythconverg</DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
</Configuration>

```
And this is /etc/mythtv/confix.xml:
```
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
        <DBHostName>Jupiter</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>mythtv</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>3306</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

```
> **blm-ubunet said:**
> The other problem could be version mismatches which you have tried to mitigate by using same mythbuntu versions..
All the backends and frontends are version 0.27.

---

### Post by blm-ubunet on 2015-05-31
Can you try
ping Jupiter
ping 192.168.1.104

These should work because you can connect to mysql server on "Jupiter" box.

I would say the problem is the master backend (combine BE & FE) is not listening on external IP addresses.

A log file from the MBE would be good.
sudo initctl stop mythtv-backend
(could run mythtv-setup & look at both IP addresses)
mythbackend.real > logfile.txt

The BE always runs as user "mythtv".
If the combined FE box runs as a user != "mythtv" then there are (3) copies of "config.xml" in play.
BE   /home/mythtv/.mythtv/config.xml
FE  /home/<other-user>/.mythtv/config.xml
fallback /etc/mythtv/config.xml

Does pay to symlink them to one file.

---

### Post by bilkay on 2015-06-01
Both backends are running under user mythtv. The PC with the master BE and a FE does not have a /home/mythtv directory nor an /etc/mythtv directory. The laptop does (don't ask me to explain). I changed the local IP address in the master BE setup from the loopback to 192.168.1.104 (from the Wiki). That had no effect whatsoever. When I start the remote frontend, I get nothing in the master BE log. I get the following in the remote FE log:
```
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27.4-68-gaad5349] www.mythtv.org
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: N thread_unknown logging.cpp:907 (logStart) Setting Log Level to LOG_INFO
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/kriebelw/.mythtv
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I Logger logging.cpp:308 (run) Added logging to the console
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythcorecontext.cpp:257 (Init) Assumed character encoding: en_US.UTF-8
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of Laptop
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'Jupiter'
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I LogForward loggingserver.cpp:1373 (forwardMessage) New Client:  (#1)
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: N CoreContext mythcorecontext.cpp:1634 (InitLocale) Setting QT default locale to en_US
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythcorecontext.cpp:1667 (SaveLocaleDefaults) Current locale en_US
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
Jun  1 16:22:37 Laptop mythfrontend.real: mythfrontend[8024]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1366x768 60.042 Hz
Jun  1 16:22:38 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP 127.0.0.1:6547
Jun  1 16:22:38 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP [::1]:6547
Jun  1 16:22:38 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP [fe80::7ae4:ff:fe39:c8a7%wlan0]:6547
Jun  1 16:22:38 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/kriebelw/.mythtv/joystickmenurc
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext serverpool.cpp:500 (bind) Binding to UDP 127.0.0.1:6948
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext serverpool.cpp:500 (bind) Binding to UDP [::1]:6948
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext serverpool.cpp:500 (bind) Binding to UDP [fe80::7ae4:ff:fe39:c8a7%wlan0]:6948
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythmainwindow.cpp:991 (Init) Using Frameless Window
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythmainwindow.cpp:1002 (Init) Using Full Screen Window
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythmainwindow.cpp:1118 (Init) Using the Qt painter
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(9518ae0:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(95730f8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(92232a8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(954ec40:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:39 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b1ef78:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(925cc68:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(9227290:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b20df8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b2ecb8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b20e10:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b343f8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(90343e0:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(926cfa0:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b32358:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythuiwebbrowser.cpp:1078 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythuiwebbrowser.cpp:991 (Init) MythUIWebBrowser: enabling plugins
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b0bed8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E CoreContext AirPlay/mythraopdevice.cpp:30 (Create) RAOP Device: Aborting startup - no key found.
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext AirPlay/mythairplayserver.cpp:371 (Create) AirPlay: Created airplay objects.
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I thread_unknown serverpool.cpp:404 (listen) Listening on TCP 127.0.0.1:5100
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I thread_unknown serverpool.cpp:404 (listen) Listening on TCP [::1]:5100
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I thread_unknown serverpool.cpp:404 (listen) Listening on TCP [fe80::7ae4:ff:fe39:c8a7%wlan0]:5100
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
Jun  1 16:22:40 Laptop mythfrontend.real: mythfrontend[8024]: I AirplayServer bonjourregister.cpp:115 (BonjourCallback) Bonjour: Service registration complete: name 'MythTV on Laptop' type '_airplay._tcp.' domain: 'local.'
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: N CoreContext mythmainwindow.cpp:1996 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: W CoreContext mythplugin.cpp:143 (MythPluginManager) No plugins directory /usr/lib/mythtv/plugins
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: N CoreContext main.cpp:1062 (RunMenu) Found mainmenu.xml for theme 'Mythbuntu'
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b30b58:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(962f3d8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(9630228:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: E CoreContext mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext themechooser.cpp:1038 (ThemeUpdateChecker) Checking for theme updates every hour
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'HardwareProfiler'.
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext housekeeper.cpp:655 (Start) Starting HouseKeeper.
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: I Reconnect mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b30ce8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: E Reconnect mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b21030:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:42 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext bonjourregister.cpp:115 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on Laptop' type '_mythfrontend._tcp.' domain: 'local.'
Jun  1 16:22:46 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:46 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b2f770:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:46 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:46 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:46 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(9621550:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:46 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:47 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:47 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(95bede8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:47 Laptop mythfrontend.real: mythfrontend[8024]: E CoreContext mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:47 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:47 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b21030:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:47 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:47 Laptop mythfrontend.real: mythfrontend[8024]: I Reconnect mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:47 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b2ed08:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:47 Laptop mythfrontend.real: mythfrontend[8024]: E Reconnect mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:52 Laptop mythfrontend.real: mythfrontend[8024]: I Reconnect mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:52 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b2f770:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:52 Laptop mythfrontend.real: mythfrontend[8024]: E Reconnect mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:57 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:57 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(972a0f8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:57 Laptop mythfrontend.real: mythfrontend[8024]: E CoreContext mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:22:57 Laptop mythfrontend.real: mythfrontend[8024]: I Reconnect mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:22:57 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b20fb8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:22:57 Laptop mythfrontend.real: mythfrontend[8024]: E Reconnect mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:02 Laptop mythfrontend.real: mythfrontend[8024]: I Reconnect mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:02 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b21030:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:02 Laptop mythfrontend.real: mythfrontend[8024]: E Reconnect mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:03 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:03 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b21030:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:03 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:07 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext bonjourregister.cpp:28 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on Laptop'
Jun  1 16:23:07 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext AirPlay/mythraopdevice.cpp:71 (Cleanup) RAOP Device: Cleaning up.
Jun  1 16:23:07 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext AirPlay/mythairplayserver.cpp:377 (Cleanup) AirPlay: Cleaning up.
Jun  1 16:23:07 Laptop mythfrontend.real: mythfrontend[8024]: I thread_unknown bonjourregister.cpp:28 (~BonjourRegister) Bonjour: De-registering service '_airplay._tcp.' on 'MythTV on Laptop'
Jun  1 16:23:07 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext main.cpp:262 (cleanup) Shutting down UPnP client...
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b36c08:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b2ed98:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I CoreContext mythcontext.cpp:1194 (~MythContext) Waiting for threads to exit.
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(915bcf8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(91f1b58:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b30ce8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b30bd8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(921ef00:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b1f118:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(923e6f0:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b1f0d8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b1f0d8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(92595e0:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b1f0d8:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(91f1b58:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: I SendMessage mythcorecontext.cpp:426 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E MythSocketThread(-1) mythsocket.cpp:721 (ConnectToHostReal) MythSocket(ffffffffb3b32130:-1): Failed to connect to (192.168.1.104:6543) Connection refused
Jun  1 16:23:08 Laptop mythfrontend.real: mythfrontend[8024]: E SendMessage mythcorecontext.cpp:496 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address

```

---

### Post by bilkay on 2015-06-01
I'm flailing around in the dark here, but if the FE is trying to connect via port 6543, shouldn't there be an entry for that port in the master's /etc/services file?

---

### Post by tgm4883 on 2015-06-01
I'm going to try and help here, but you aren't real clear with what you are doing with your tests so I'm going to have you gather some semi-specific info.

On your master backend, please run the following commands and post their output here.

```

lsb_release -a
ip addr
ping jupiter
mysql -h Jupiter -u mythtv -D mythconverg -p
telnet -tulpn

```

On the frontend that won't connect, please run the following commands and post the output here.
```

lsb_release -a
ip addr
ping jupiter
mysql -h Jupiter -u mythtv -D mythconverg -p
telnet jupiter 3306

```

---

### Post by bilkay on 2015-06-02
> **tgm4883 said:**
> I'm going to try and help here, but you aren't real clear with what you are doing with your tests so I'm going to have you gather some semi-specific info.

On your master backend, please run the following commands and post their output here.

```

lsb_release -a
ip addr
ping jupiter
mysql -h Jupiter -u mythtv -D mythconverg -p
telnet -tulpn

```

```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

```
```

$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 44:8a:5b:ce:50:a8 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.104/24 brd 192.168.1.255 scope global eth1
       valid_lft forever preferred_lft forever
    inet6 fe80::468a:5bff:fece:50a8/64 scope link 
       valid_lft forever preferred_lft forever

```
```

$ ping -c 1 jupiter
PING Jupiter.localdomain (127.0.1.1) 56(84) bytes of data.
64 bytes from Jupiter.localdomain (127.0.1.1): icmp_seq=1 ttl=64 time=0.018 ms

--- Jupiter.localdomain ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms

rtt min/avg/max/mdev = 0.018/0.018/0.018/0.000 ms

```
```

$ mysql -h Jupiter -u mythtv -D mythconverg -p
Enter password: 
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 626
Server version: 5.5.43-0ubuntu0.14.04.1 (Ubuntu)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>

```
```

$ telnet -tulpn
telnet: Warning: -t ignored, no TN3270 support.
telnet>

```
> **tgm4883 said:**
> 
On the frontend that won't connect, please run the following commands and post the output here.
```

lsb_release -a
ip addr
ping jupiter
mysql -h Jupiter -u mythtv -D mythconverg -p
telnet jupiter 3306

```
```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

```
```

$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether c8:0a:a9:6f:38:c0 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 78:e4:00:39:c8:a7 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.102/24 brd 192.168.1.255 scope global wlan0
    inet6 fe80::7ae4:ff:fe39:c8a7/64 scope link 
       valid_lft forever preferred_lft forever

```
```

$ ping -c 1 jupiter
PING Jupiter (192.168.1.104) 56(84) bytes of data.
64 bytes from Jupiter (192.168.1.104): icmp_req=1 ttl=64 time=1.02 ms

--- Jupiter ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.024/1.024/1.024/0.000 ms

```
```

$ mysql -h Jupiter -u mythtv -D mythconverg -p
Enter password: 
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 627
Server version: 5.5.43-0ubuntu0.14.04.1 (Ubuntu)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>

```
```

$ telnet jupiter 3306
Trying 192.168.1.104...
Connected to Jupiter.
Escape character is '^]'.
[
5.5.43-0ubuntu0.14.04.1t<n5^Z)[&#65533;6cn"XxqOw,rymysql_native_passwordConnection closed by foreign host.

```

---

### Post by blm-ubunet on 2015-06-02
The MasterBE must have either /etc/mythtv/config.xml or one in /home/mythtv/.mythtv/..
Did you not post this before (post #4) ?

You have to use "sudo" with your FE user to snoop inside files of other /home folders.

What resolves "Jupiter" to an IP address on the MBE ?
"/etc/hosts" or your router/DNS ?

---

### Post by bilkay on 2015-06-02
> **blm-ubunet said:**
> The MasterBE must have either /etc/mythtv/config.xml or one in /home/mythtv/.mythtv/..
Did you not post this before (post #4) ?

As I noted earlier, neither DIRECTORY exists on the MBE machine (there is no /home/mythtv). I don't understand why the installation created them on the Laptop but not on Jupiter. There is, however, a .mythtv/config.xml file in my home directory.
> **blm-ubunet said:**
> 
You have to use "sudo" with your FE user to snoop inside files of other /home folders.

What resolves "Jupiter" to an IP address on the MBE ?
"/etc/hosts" or your router/DNS ?
/etc/hosts

---

### Post by blm-ubunet on 2015-06-03
I think the MBE is still binding/listening on link-local 127.0.0.1 only.
Can we see the log from MBE as it starts ?
Let it start via normal upstart job so can see the correct "user" & which config.xml file is used.

How old is this install ? Does it pre-date the changeover from .txt file to config.xml ?

---

### Post by tgm4883 on 2015-06-03
Whoops, a typo in one of my commands. Can you post the output from the following command from the backend

```

netstat -tulpn

```

---

### Post by bilkay on 2015-06-04
> **tgm4883 said:**
> Whoops, a typo in one of my commands. Can you post the output from the following command from the backend

```

netstat -tulpn

```

```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.1.104:6547      0.0.0.0:*               LISTEN      16809/mythfrontend.
tcp        0      0 127.0.0.1:6547          0.0.0.0:*               LISTEN      16809/mythfrontend.
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1364/dnsmasq    
tcp        0      0 0.0.0.0:45685           0.0.0.0:*               LISTEN      1273/rpc.mountd 
tcp        0      0 0.0.0.0:55542           0.0.0.0:*               LISTEN      633/rpc.statd   
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      7956/cupsd      
tcp        0      0 0.0.0.0:6551            0.0.0.0:*               LISTEN      2945/skype      
tcp        0      0 0.0.0.0:12023           0.0.0.0:*               LISTEN      1040/sshd       
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1398/sendmail: MTA:
tcp        0      0 0.0.0.0:35003           0.0.0.0:*               LISTEN      1273/rpc.mountd 
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      609/smbd        
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      18505/mysqld    
tcp        0      0 0.0.0.0:48938           0.0.0.0:*               LISTEN      1273/rpc.mountd 
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN      1398/sendmail: MTA:
tcp        0      0 0.0.0.0:56939           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      609/smbd        
tcp        0      0 192.168.1.104:5100      0.0.0.0:*               LISTEN      16809/mythfrontend.
tcp        0      0 127.0.0.1:5100          0.0.0.0:*               LISTEN      16809/mythfrontend.
tcp        0      0 127.0.0.1:6543          0.0.0.0:*               LISTEN      2198/mythbackend
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      616/rpcbind     
tcp        0      0 127.0.0.1:6544          0.0.0.0:*               LISTEN      2198/mythbackend
tcp6       0      0 fe80::468a:5bff:fe:6547 :::*                    LISTEN      16809/mythfrontend.
tcp6       0      0 ::1:6547                :::*                    LISTEN      16809/mythfrontend.
tcp6       0      0 ::1:631                 :::*                    LISTEN      7956/cupsd      
tcp6       0      0 :::59703                :::*                    LISTEN      1273/rpc.mountd 
tcp6       0      0 :::12023                :::*                    LISTEN      1040/sshd       
tcp6       0      0 :::445                  :::*                    LISTEN      609/smbd        
tcp6       0      0 :::2049                 :::*                    LISTEN      -               
tcp6       0      0 :::51010                :::*                    LISTEN      633/rpc.statd   
tcp6       0      0 :::39080                :::*                    LISTEN      -               
tcp6       0      0 :::139                  :::*                    LISTEN      609/smbd        
tcp6       0      0 fe80::468a:5bff:fe:5100 :::*                    LISTEN      16809/mythfrontend.
tcp6       0      0 ::1:5100                :::*                    LISTEN      16809/mythfrontend.
tcp6       0      0 :::55021                :::*                    LISTEN      1273/rpc.mountd 
tcp6       0      0 :::48462                :::*                    LISTEN      1273/rpc.mountd 
tcp6       0      0 fe80::468a:5bff:fe:6543 :::*                    LISTEN      2198/mythbackend
tcp6       0      0 ::1:6543                :::*                    LISTEN      2198/mythbackend
tcp6       0      0 :::111                  :::*                    LISTEN      616/rpcbind     
tcp6       0      0 fe80::468a:5bff:fe:6544 :::*                    LISTEN      2198/mythbackend
tcp6       0      0 ::1:6544                :::*                    LISTEN      2198/mythbackend
tcp6       0      0 :::80                   :::*                    LISTEN      1722/apache2    
udp        0      0 0.0.0.0:62953           0.0.0.0:*                           15178/dhclient  
udp        0      0 0.0.0.0:57842           0.0.0.0:*                           1273/rpc.mountd 
udp        0      0 0.0.0.0:2049            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:52757           0.0.0.0:*                           1273/rpc.mountd 
udp        0      0 127.0.1.1:53            0.0.0.0:*                           1364/dnsmasq    
udp        0      0 0.0.0.0:41533           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           15178/dhclient  
udp        0      0 127.0.0.1:46155         0.0.0.0:*                           2945/skype      
udp        0      0 0.0.0.0:111             0.0.0.0:*                           616/rpcbind     
udp        0      0 0.0.0.0:631             0.0.0.0:*                           997/cups-browsed
udp        0      0 192.168.1.104:123       0.0.0.0:*                           15343/ntpd      
udp        0      0 127.0.0.1:123           0.0.0.0:*                           15343/ntpd      
udp        0      0 0.0.0.0:123             0.0.0.0:*                           15343/ntpd      
udp        0      0 192.168.1.255:137       0.0.0.0:*                           1642/nmbd       
udp        0      0 192.168.1.104:137       0.0.0.0:*                           1642/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1642/nmbd       
udp        0      0 192.168.1.255:138       0.0.0.0:*                           1642/nmbd       
udp        0      0 192.168.1.104:138       0.0.0.0:*                           1642/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1642/nmbd       
udp        0      0 0.0.0.0:34995           0.0.0.0:*                           633/rpc.statd   
udp        0      0 0.0.0.0:51929           0.0.0.0:*                           1273/rpc.mountd 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           654/avahi-daemon: r
udp        0      0 0.0.0.0:37634           0.0.0.0:*                           654/avahi-daemon: r
udp        0      0 0.0.0.0:778             0.0.0.0:*                           616/rpcbind     
udp        0      0 192.168.1.255:6948      0.0.0.0:*                           16809/mythfrontend.
udp        0      0 192.168.1.104:6948      0.0.0.0:*                           16809/mythfrontend.
udp        0      0 127.0.0.1:6948          0.0.0.0:*                           16809/mythfrontend.
udp        0      0 127.0.0.1:809           0.0.0.0:*                           633/rpc.statd   
udp        0      0 255.255.255.255:1900    0.0.0.0:*                           16809/mythfrontend.
udp        0      0 239.255.255.250:1900    0.0.0.0:*                           16809/mythfrontend.
udp        0      0 0.0.0.0:6549            0.0.0.0:*                           16809/mythfrontend.
udp        0      0 0.0.0.0:6551            0.0.0.0:*                           2945/skype      
udp6       0      0 :::2049                 :::*                                -               
udp6       0      0 :::53855                :::*                                1273/rpc.mountd 
udp6       0      0 :::43626                :::*                                -               
udp6       0      0 :::111                  :::*                                616/rpcbind     
udp6       0      0 fe80::468a:5bff:fec:123 :::*                                15343/ntpd      
udp6       0      0 ::1:123                 :::*                                15343/ntpd      
udp6       0      0 :::123                  :::*                                15343/ntpd      
udp6       0      0 :::57479                :::*                                15178/dhclient  
udp6       0      0 :::58509                :::*                                633/rpc.statd   
udp6       0      0 :::5353                 :::*                                654/avahi-daemon: r
udp6       0      0 :::778                  :::*                                616/rpcbind     
udp6       0      0 fe80::468a:5bff:fe:6948 :::*                                16809/mythfrontend.
udp6       0      0 ::1:6948                :::*                                16809/mythfrontend.
udp6       0      0 :::33079                :::*                                1273/rpc.mountd 
udp6       0      0 :::57701                :::*                                654/avahi-daemon: r
udp6       0      0 :::55726                :::*                                1273/rpc.mountd 


```

---

### Post by bilkay on 2015-06-04
> **blm-ubunet said:**
> I think the MBE is still binding/listening on link-local 127.0.0.1 only.
Can we see the log from MBE as it starts ?
Let it start via normal upstart job so can see the correct "user" & which config.xml file is used.

I don't know what you mean by "Let it start via normal upstart job". I stopped and restarted it by running the setup. There were no entries in /var/log/mythtv/mythbackend.log and the following in myth-setup.log:
```

Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythtv-setup version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.6, runtime: 4.8.6
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/me/.mythtv
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I Logger logging.cpp:315 (run) Added logging to the console
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of Jupiter
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to en_US
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale en_US
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/me/.mythtv/joystickmenurc
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 127.0.0.1:6948
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 192.168.1.104:6948
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [::1]:6948
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [fe80::468a:5bff:fece:50a8%eth1]:6948
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 192.168.1.255:6948
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythmainwindow.cpp:973 (Init) Using Frameless Window
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythmainwindow.cpp:986 (Init) Using Full Screen Window
Jun  4 18:42:59 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythmainwindow.cpp:1077 (Init) Using the Qt painter
Jun  4 18:43:01 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythuiwebbrowser.cpp:1078 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Jun  4 18:43:01 Jupiter mythtv-setup.real: mythtv-setup[16705]: E CoreContext mythuiwebbrowser.cpp:962 (Init) MythUIWebBrowser: failed to find our parent screen
Jun  4 18:43:01 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythuiwebbrowser.cpp:991 (Init) MythUIWebBrowser: enabling plugins
Jun  4 18:43:01 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Jun  4 18:43:01 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythcorecontext.cpp:423 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.104:6543 (try 1 of 1)
Jun  4 18:43:01 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythcorecontext.cpp:1241 (CheckProtoVersion) Using protocol version 77
Jun  4 18:43:05 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext startprompt.cpp:52 (stopBackend) Trying to stop backend
Jun  4 18:43:05 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythmainwindow.cpp:2590 (LockInputDevices) Locking input devices
Jun  4 18:43:05 Jupiter mythtv-setup.real: mythtv-setup[16705]: N CoreContext mythmainwindow.cpp:2638 (PauseIdleTimer) Suspending idle timer
Jun  4 18:43:06 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythmainwindow.cpp:2592 (LockInputDevices) Unlocking input devices
Jun  4 18:43:06 Jupiter mythtv-setup.real: mythtv-setup[16705]: N CoreContext mythmainwindow.cpp:2643 (PauseIdleTimer) Resuming idle timer
Jun  4 18:43:09 Jupiter mythtv-setup.real: mythtv-setup[16705]: E CoreContext checksetup.cpp:166 (checkImageStoragePaths) You have a Video Storage Group, but have not set up all Image Groups.  If you continue, video image downloads will be saved in your Videos Storage Group.  Do you want to store them in their own groups?
Jun  4 18:43:13 Jupiter mythtv-setup.real: mythtv-setup[16705]: E CoreContext exitprompt.cpp:130 (quit) backendrestartmythbackend
Jun  4 18:43:13 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythmainwindow.cpp:2590 (LockInputDevices) Locking input devices
Jun  4 18:43:13 Jupiter mythtv-setup.real: mythtv-setup[16705]: N CoreContext mythmainwindow.cpp:2638 (PauseIdleTimer) Suspending idle timer
Jun  4 18:43:21 Jupiter mythtv-setup.real: mythtv-setup[16705]: E CoreContext exitprompt.cpp:130 (quit) backendrestartmythbackend
Jun  4 18:43:21 Jupiter mythtv-setup.real: mythtv-setup[16705]: I CoreContext mythmainwindow.cpp:2590 (LockInputDevices) Locking input devices
Jun  4 18:43:21 Jupiter mythtv-setup.real: mythtv-setup[16705]: N CoreContext mythmainwindow.cpp:2638 (PauseIdleTimer) Suspending idle timer


```
> **blm-ubunet said:**
> How old is this install ? Does it pre-date the changeover from .txt file to config.xml ?
I installed it this year.

---

### Post by tgm4883 on 2015-06-04
> **bilkay said:**
> ```

tcp        0      0 127.0.0.1:6543          0.0.0.0:*               LISTEN      2198/mythbackend     
tcp        0      0 127.0.0.1:6544          0.0.0.0:*               LISTEN      2198/mythbackend

```

There is your problem. You need to fire up mythtv-setup and tell it to use your private IP address (not 127.0.0.1, and not jupiter since that resolves locally). Once you do that it should be listening on all interfaces and your other frontend should connect.

---

### Post by bilkay on 2015-06-05
> **tgm4883 said:**
> There is your problem. You need to fire up mythtv-setup and tell it to use your private IP address (not 127.0.0.1, and not jupiter since that resolves locally). Once you do that it should be listening on all interfaces and your other frontend should connect.
Got it working. MBE needed a reboot.

Thanks!

---

