---
title: "Securing MythWeb issue"
date: 2016-04-17
forum: Mythbuntu
---

### Post by mapota on 2016-04-17
[COLOR=#000000][FONT=Verdana]Hi All, [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]I am having trouble running MCC and securing mythweb. [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]I change the option to enable, enter a username password and hot apply. It [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]asks for confirmation then to authenticate. But then I get the following [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]error. [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]DBus Exception [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]Org.freedesktop.DBus.Python.configparser.NoSectionError [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Traceback (most recent call last): [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]File "/usr/lib/python3.4/configparser.py", line 877, in set [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]sectdict = self._sections[section] [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]KeyError: 'cfg' [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]During handling of the above exception, another exception occurred: [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]Traceback (most recent call last): [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]File "/usr/lib/python3/dist-packages/dbus/service.py", line 707, in [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]_message_cb [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]retval = candidate_method(self, *args, **keywords) [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]File "/usr/lib/python3/dist-packages/MythbuntuControlCentre/backend.py", [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]line 280, in scriptedchanges [/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana]plugin_instances[instance].root_scripted_changes(plugin_dictionary[plugin]) [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]File "/usr/share/mythbuntu/plugins/python/plugins.py", line 188, in [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]root_scripted_changes [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]self.config.set("cfg", "password", reconfigure[item]) [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]File "/usr/lib/python3.4/configparser.py", line 1167, in set [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]super().set(section, option, value) [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]File "/usr/lib/python3.4/configparser.py", line 879, in set [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]raise NoSectionError(section) [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]configparser.NoSectionError: No section: 'cfg' [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]I did find an old thread with Mcc issues to do with backups. So I have [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]checked some of the same things. [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]dpkg -l mythbuntu-common [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]returns [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]Desired=Unknown/Install/Remove/Purge/Hold [/FONT][/COLOR]

[COLOR=#660066][FONT=Verdana]| 
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend [/FONT][/COLOR]

[COLOR=#660066][FONT=Verdana]|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) 
[/FONT][/COLOR]
[COLOR=#007777][FONT=Verdana]||/ Name Version Architecture 
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Description [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]+++-=========================-=================-=================-========== [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]============================================= 
[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii mythbuntu-common 0.74 all Mythbuntu [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]application support functions [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]dpkg -l mythbuntu-bare-client [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]returns [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]Desired=Unknown/Install/Remove/Purge/Hold [/FONT][/COLOR]

[COLOR=#660066][FONT=Verdana]| 
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend [/FONT][/COLOR]

[COLOR=#660066][FONT=Verdana]|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) 
[/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]||/ Name Version Architecture 
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Description [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]+++-=========================-=================-=================-========== [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]============================================= 
[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii mythbuntu-bare-client 2.6.3 all Mythbuntu [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Bare Client [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]Hope this helps. [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]I was unsure about downloading the patch as I already have 2.6.3 [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I am running 14.04.4 LTS of mythbuntu [/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana]MythTV Version : v0.27.6-17-g815cab6 [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]MythTV Branch : fixes/0.27 [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Network Protocol : 77 [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Library API : 0.27.20151025-1 [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]QT Version : 4.8.6 [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Options compiled in: [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]linux profile use_hidesyms using_alsa using_oss using_pulse [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]using_pulseoutput using_backend using_bindings_perl using_bindings_python [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]using_bindings_php using_crystalhd using_dvb using_firewire using_frontend [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]using_hdhomerun using_ceton using_hdpvr using_ivtv using_joystick_menu [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]using_libcrypto using_libdns_sd using_libfftw3 using_libxml2 using_lirc [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]using_mheg using_opengl using_opengl_video using_qtwebkit using_qtscript [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]using_qtdbus using_sdl using_taglib using_v4l2 using_x11 using_xrandr [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]using_xv using_profiletype using_bindings_perl using_bindings_python [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]using_bindings_php using_mythtranscode using_opengl using_vaapi using_vdpau [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]using_ffmpeg_threads using_mheg using_libass using_libxml2 [/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana]Thanks for any help you can give.[/FONT][/COLOR]

---

