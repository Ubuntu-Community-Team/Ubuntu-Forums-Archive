---
title: "After updating 0.26, unable to start frontend"
date: 2013-03-26
forum: Mythbuntu
---

### Post by mapota on 2013-03-26
[COLOR=#000000][FONT=verdana]Hi All,[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I just allowed the latest update to be done on my back end and front end. The back end worked fine so all good there, but the frontend stalled and the box locked up. No response to keyboard mouse etc. So rebooted but now the frontend will not start fully. I just get a blank background. No menus or background image.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]How do I get the update to restart? [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I tried [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]sudo apt-get update && apt-get upgrade [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]but that only checked the mythbuntu stuff.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Also tried disabling updates in MCC, applying and then re-enabling and applying, but update centre thinks still up to date. How do I rewind where it thinks it is up to?

Any help appreciated.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Edit: Sorry should state on mythbuntu 12.04 and mythtv 0.26+fixes[/FONT][/COLOR]



Second Edit:

[COLOR=#000000][FONT=verdana]I use the glass theme and can only see that background colour not any background image or menu items.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Andrew[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Edit:: did try starting from a terminal session just now and got the following[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]lounge@Lounge-Front-End:~$ mythfrontend[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]/usr/bin/mythfrontend: 41: /usr/bin/mythfrontend: Syntax error: "done" unexpected[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]Then tried the following[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]lounge@Lounge-Front-End:~$ mythfrontend.real[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]QGtkStyle was unable to detect the current GTK+ theme.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.467936 I Setup Interrupt handler[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.468085 I Setup Terminated handler[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.468143 I Setup Segmentation fault handler[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.468190 I Setup Aborted handler[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.468235 I Setup Bus error handler[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.468276 I Setup Floating point exception handler[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.468322 I Setup Illegal instruction handler[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.468367 I Setup Real-time signal 0 handler[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.468423 I Setup User defined signal 1 handler[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.468472 I Setup User defined signal 2 handler[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.468914 C mythfrontend version: fixes/0.26 [v0.26.0-137-g5fe87ed] [/FONT][/COLOR][www.mythtv.org]("http://www.mythtv.org/")
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.468960 C Qt version: compile: 4.8.1, runtime: 4.8.1[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.468988 N Enabled verbose msgs: general[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.469068 N Setting Log Level to LOG_INFO[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.470618 I Added logging to the console[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.473611 N Using runtime prefix = /usr[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.473698 N Using configuration directory = /home/lounge/.mythtv[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.476001 I Assumed character encoding: en_AU.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.480207 N Empty LocalHostName.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.480239 I Using localhost value of Lounge-Front-End[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.480350 I Testing network connectivity to '192.168.1.66'[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.481388 I Starting process manager[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.481801 I Starting process signal handler[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.481986 I Starting IO manager (read)[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.482091 I Starting IO manager (write)[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.639391 N Setting QT default locale to en_AU[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.639596 I Current locale en_AU[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.640172 E No locale defaults file for en_AU, skipping[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.683817 I ScreenSaverX11Private: XScreenSaver support enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.687186 I ScreenSaverX11Private: DPMS is disabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.711662 I Starting mythlogserver[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:12.736322 N Desktop video mode: 1920x1080 60.000 Hz[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.028903 I Listening on TCP 127.0.0.1:6547[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.030243 I Listening on TCP 192.168.1.77:6547[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.030545 I Listening on TCP [::1]:6547[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.030884 I Listening on TCP [fe80::201:2eff:fe27:f2f6%eth0]:6547[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.284202 I Added logging to mythlogserver at TCP:35327[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]cannot find libcec.solibcec.so: cannot open shared object file: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.816922 I RAOP Device: Created RAOP device objects.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.817494 I Listening on TCP 127.0.0.1:5000[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.817722 I Listening on TCP 192.168.1.77:5000[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.817973 I Listening on TCP [::1]:5000[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.818217 I Listening on TCP [fe80::201:2eff:fe27:f2f6%eth0]:5000[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.818313 I RAOP Device: Listening for connections on port 5000[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.819259 I AirPlay: Created airplay objects.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.819756 I Listening on TCP 127.0.0.1:5100[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.819969 I Listening on TCP 192.168.1.77:5100[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.820215 I Listening on TCP [::1]:5100[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.820458 I Listening on TCP [fe80::201:2eff:fe27:f2f6%eth0]:5100[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.823999 I Registering service 6f474f556c45@MythTV on Lounge-Front-End._raop._tcp port 5000 TXT tp=UDsm=falssv=falseek=1et=0,1cn=0,1ch=2ss=1sr=441 0pw=falsevn=3	txtvers=md=0,1,2 vs=130.14da=true[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.835542 I Loading en_us translation for module mythfrontend[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.870538 I LIRC: Successfully initialized '/dev/lircd' using '/home/lounge/.mythtv/lircrc' config[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.871008 E JoystickMenuThread: Joystick disabled - Failed to read /home/lounge/.mythtv/joystickmenurc[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.893032 E CECAdapter: Failed to load libcec.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.893105 I UDPListener: Enabling[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.895705 I Binding to UDP 127.0.0.1:6948[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.896081 I Binding to UDP 192.168.1.77:6948[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.896508 I Binding to UDP [::1]:6948[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.896986 I Binding to UDP [fe80::201:2eff:fe27:f2f6%eth0]:6948[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:13.897401 I Binding to UDP 192.168.1.255:6948[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:14.014035 I Using Frameless Window[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:14.014151 I Using Full Screen Window[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:14.377688 I Using the Qt painter[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:14.652352 I Bonjour: Service registration complete: name 'MythTV on Lounge-Front-End' type '_airplay._tcp.' domain: 'local.'[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:14.659810 I Bonjour: Service registration complete: name '6f474f556c45@MythTV on Lounge-Front-End' type '_raop._tcp.' domain: 'local.'[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:15.269588 I Current MythTV Schema Version (DBSchemaVer): 1307[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:15.514051 W ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:15.514092 E ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:15.519007 W ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:15.519044 E ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:16.152989 N Registering Internal as a media playback plugin.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:16.309975 I Loading en_us translation for module mythgallery[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:16.354176 I Current MythMusic Schema Version (MusicDBSchemaVer): 1020[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:16.427861 I Loading en_us translation for module mythmusic[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:16.434967 I Last hardware profile update was > 30 days ago, update required...[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2013-03-27 12:22:16.435114 I Locking input devices[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]At about using Full screen window log the blank screen appears and stalls.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Andrew[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Andrew[/FONT][/COLOR]

---

### Post by tgm4883 on 2013-03-28
Please open a new thread if you have an issue regarding mythtv. The thread you posted on was for questions/issues regarding the repos.

---

