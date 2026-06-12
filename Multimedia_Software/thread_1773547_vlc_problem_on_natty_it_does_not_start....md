---
title: "vlc problem on natty it does not start..."
date: 2011-06-02
forum: Multimedia Software
---

### Post by shantiq on 2011-06-02
ok been trying for a while now so i need help with this


i tried 1.1.8 from source did not go right then i installed 1.1.9 through synaptic then tried the development version and got now so confused that i think i have completely borked it   the system does not know which one is installed


this is what i get when i try from commmand line   i have 1.1.9 installed through synaptic but i get this cryptic message


any ideas   thanx   shan

```
vlc
VLC media player 1.1.8 The Luggage (revision exported)
[0x1d5d3c0] main interface error: no suitable interface module
[0x1d5d3c0] main interface error: no suitable interface module
[0x1d0a110] main libvlc error: option http-user-agent does not exist
[0x1d5d450] main interface error: no suitable interface module
[0x1d0a110] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x1d0a110] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x1d5d8a0] main interface error: no suitable interface module
[0x1d0a110] main libvlc error: interface "default" initialization failed
shantiq@shan:~$ cvlc
VLC media player 1.1.8 The Luggage (revision exported)
[0x2092e50] main interface error: no suitable interface module
[0x2092e50] main interface error: no suitable interface module
[0x2033120] main libvlc error: option http-user-agent does not exist
[0x2092ee0] main interface error: no suitable interface module
[0x2033120] main libvlc error: interface "signals" initialization failed
[0x2092ee0] main interface error: no suitable interface module
[0x2033120] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x2092ee0] main interface error: no suitable interface module
[0x2033120] main libvlc error: interface "default" initialization failed

```


this here shows the system is confused about the version installed    how can i get out of this

```
vlc -vvv
VLC media player 1.1.8 The Luggage (revision exported)
[0x6e1110] main libvlc debug: VLC media player - 1.2.0-git Twoflower
[0x6e1110] main libvlc debug: Copyright © 1996-2011 the VideoLAN team
[0x6e1110] main libvlc debug: revision 6436e12
[0x6e1110] main libvlc debug: configured with ./configure  '--prefix=/usr/local' '--with-live555-tree=/home/shantiq/vlc_build/live' '--enable-real' '--enable-realrtsp' '--enable-aa' '--enable-merge-ffmpeg' '--enable-vcdx' '--enable-ncurses' 'PKG_CONFIG_PATH=/home/shantiq/vlc_build/vlcdeps/usr/lib/pkgconfig'
[0x6e1110] main libvlc debug: translation test: code is "en_GB"
[0x6e1110] main libvlc debug: checking plugin modules
[0x6e1110] main libvlc debug: loading plugins cache file /usr/local/lib/vlc/plugins/plugins.dat
[0x6e1110] main libvlc warning: cannot read /usr/local/lib/vlc/plugins/plugins.dat (No such file or directory)
[0x6e1110] main libvlc debug: recursively browsing `/usr/local/lib/vlc/plugins'
[0x6e1110] main libvlc warning: cannot find symbol "vlc_entry__1_2_0h" in plugin `/usr/local/lib/vlc/plugins/access/libdvb_plugin.so'
[0x6e1110] main libvlc debug: saving plugins cache /usr/local/lib/vlc/plugins/plugins.dat
[0x6e1110] main libvlc debug: module bank initialized (7 modules)
[0x6e1110] main libvlc debug: opening config file (/home/shantiq/.config/vlc/vlcrc)
[0x6e1110] main libvlc debug: CPU has capabilities MMX 3DNow! MMXEXT SSE SSE2 SSE3 FPU 
[0x6e1110] main libvlc debug: looking for memcpy module: 0 candidates
[0x6e1110] main libvlc debug: no memcpy module matched "any"
[0x734420] main interface debug: looking for interface module: 0 candidates
[0x734420] main interface debug: no interface module matched "hotkeys,none"
[0x734420] main interface debug: TIMER module_need() : 0.055 ms - Total 0.055 ms / 1 intvls (Avg 0.055 ms)
[0x734420] main interface error: no suitable interface module
[0x734420] main interface debug: looking for interface module: 0 candidates
[0x734420] main interface debug: no interface module matched "inhibit,none"
[0x734420] main interface debug: TIMER module_need() : 0.049 ms - Total 0.049 ms / 1 intvls (Avg 0.049 ms)
[0x734420] main interface error: no suitable interface module
[0x6e1110] main libvlc error: option http-user-agent does not exist
[0x7344b0] main interface debug: looking for interface module: 0 candidates
[0x7344b0] main interface debug: no interface module matched "globalhotkeys,none"
[0x7344b0] main interface debug: TIMER module_need() : 0.050 ms - Total 0.050 ms / 1 intvls (Avg 0.050 ms)
[0x7344b0] main interface error: no suitable interface module
[0x6e1110] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x6e1110] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x734900] main interface debug: looking for interface module: 0 candidates
[0x734900] main interface debug: no interface module matched "any"
[0x734900] main interface debug: TIMER module_need() : 0.048 ms - Total 0.048 ms / 1 intvls (Avg 0.048 ms)
[0x734900] main interface error: no suitable interface module
[0x6e1110] main libvlc error: interface "default" initialization failed
[0x6e1110] main libvlc debug: deactivating the playlist
[0x6e1110] main libvlc debug: removing all services discovery tasks
[0x6e1110] main libvlc debug: removing all interfaces
[0x6e1110] main libvlc debug: exiting
[0x731c40] main playlist debug: destroying
[0x6e1110] main libvlc debug: removing stats

```


attached synaptic screenshot

---

### Post by andrew.46 on 2011-06-02
I suspect you may have a copy of vlc in /usr/local as well as /usr. Have a look at the results of the following on your system:

```

$ **[COLOR="Red"]sudo find /usr -iname vlc[/COLOR]**
/usr/doc/vlc
/usr/bin/vlc
/usr/include/vlc
/usr/share/vlc
/usr/lib/vlc

```

and if I am right your results will show 2 installations...

---

### Post by shantiq on 2011-06-02
well thaNK you Andrew but i have reinstalled since i was so stuck

the 1.1.9 on natty still does not work  (freezes the whole system after crunching noises)so i have installed development 1.2 two-flower


will keep the info you provided for other time :KS


the A/V sync is still present tho maybe it is a problem with 64-bit


not sure

---

