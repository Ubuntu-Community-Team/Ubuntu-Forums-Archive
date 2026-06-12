---
title: "usb evdo rev.A modem"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by fxlovers on 2010-03-22
Dear all,

please help me to fix the problem, i used ubuntu 9.10 and i have skytech m110 cdma modem.

i already setting my conection with network manager, but it always says disconected...


> 

   [Dialer mobi]
   
  Init1 = ATZ
   
  Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
   
  Init3 = AT+CGDCONT=1,"IP","unlimited"
   
  Modem Type = Analog Modem
   
  ISDN = 0
   
  Phone = #777
   
  New PPPD = yes
   
  Modem = /dev/ttyUSB0
   
  Username = XXX
   
  Password = XXX

Baud = 460800
   
  Carrier Check = no
   
  Ask Password = 0 
   
  Dial Command = ATDT 
   
  Stupid Mode = 0
  > 

   bagoesh@bagoesh-laptop:~$ sudo wvdial mobi
  
  --> WvDial: Internet dialer version 1.60
  
  --> Cannot get information for serial port.
  
  --> Initializing modem.
  
  --> Sending: ATZ
  
  OK
  
  --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
  
  ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
  
  OK
  
  --> Modem initialized.
  
  --> Idle Seconds = 300, disabling automatic reconnect.
  
  --> Sending: ATDT#777
  
  --> Waiting for carrier.
  
  ATDT#777
  
  CONNECT 3100000
  
  --> Carrier detected.  Starting PPP immediately.
  
  --> Starting pppd at Mon Mar 22 23:03:19 2010
  
  --> Pid of pppd: 2033
  
  --> Using interface ppp0
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> Using interface ppp0
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> Using interface ppp0
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> Using interface ppp0
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> Using interface ppp0
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> Using interface ppp0
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> Using interface ppp0
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> Using interface ppp0
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> Using interface ppp0
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> Using interface ppp0
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> pppd: &#65533;dP xsP &#65533;sP X'P  
  
  --> Disconnecting at Mon Mar 22 23:04:09 2010
  
  --> The PPP daemon has died: Authentication error.
  
  --> We failed to authenticate ourselves to the peer.
  
  --> Maybe bad account or password? (exit code = 19)
  
  --> man pppd explains pppd error codes in more detail.
  
  --> I guess that's it for now, exiting
  
  [FONT=&quot]--> The PPP daemon has died. (exit code = 19)[/FONT]  then i remove ppp option


sudo aptitude remove /etc/ppp/option


then the result....

  


> 

   XXX@bXXX-laptop:~$ sudo wvdial mobi
  
  --> WvDial: Internet dialer version 1.60
  
  --> Cannot get information for serial port.
  
  --> Initializing modem.
  
  --> Sending: ATZ
  
  ~[7f]}#@!}!}!} }5}"}&} }*} } }#}%B#}%}%}&r(5@be~~[7f]}#@!}!}"} }5}"}&} }*} } }#}%B#}%}%}&r(5@ [0c]~~[7f]}#@!}!}#} }5}"}&} }*} } }#}%B#}%}%}&r(5@_S~~[7f]}#@!}!}$} }5}"}&} }*} } }#}%B#}%}%}&r(5@__~~[7f]}#@!}!}%} }5}"}&} }*} } }#}%B#}%}%}&r(5@}) ~~[7f]}#@!}!}&} }5}"}&} }*} } }#}%B#}%}%}&r(5@bi~~[7f]}#@!}!}'} }5}"}&} }*} } }#}%B#}%}%}&r(5@46~~[7f]}#@!}!}(} }5}"}&} }*} } }#}%B#}%}%}&r(5@bp~~[7f]}#@!}!})} }5}"}&} }*} } }#}%B#}%}%}&r(5@4/~~[7f]}#@!}!}*} }5}"}&} }*} } }#}%B#}%}%}&r(5@_F~~[7f]}#@!}%}*} }$[1b]n~
  
  --> Sending: ATQ0
  
  --> Re-Sending: ATZ
  
  ~[7f]}#@!}!}!} }5}"}&} }*} } }#}%B#}%}%}&r(B< m~~[7f]}#@!}!}"} }5}"}&} }*} } }#}%B#}%}%}&r(B<b}$~~[7f]}#@!}!}#} }5}"}&} }*} } }#}%B#}%}%}&r(B<4[~~[7f]}#@!}!}$} }5}"}&} }*} } }#}%B#}%}%}&r(B<4W~~[7f]}#@!}!}%} }5}"}&} }*} } }#}%B#}%}%}&r(B<b}(~~[7f]}#@!}!}&} }5}"}&} }*} } }#}%B#}%}%}&r(B<})a~~[7f]}#@!}!}'} }5}"}&} }*} } }#}%B#}%}%}&r(B<_>~~[7f]}#@!}!}(} }5}"}&} }*} } }#}%B#}%}%}&r(B<})x~~[7f]}#@!}!})} }5}"}&} }*} } }#}%B#}%}%}&r(B<_'~~[7f]}#@!}!}*} }5}"}&} }*} } }#}%B#}%}%}&r(B<4N~~[7f]}#@!}%}*} }$[1b]n~
  
  --> Modem not responding.
  
  

---

### Post by GeorgeVita on 2010-03-22
Hi **fxlovers**,
an idea is to restore /etc/ppp/option file and check if APN=unlimited username and  password are correct (ASK your provider). Also try setting 'Stupid mode = 1".

Retry and post results. Also post country, name of your provider and type of account (prepaid/contract).

Regards,
George

---

### Post by fxlovers on 2010-03-22
> **GeorgeVita said:**
> Hi **fxlovers**,
an idea is to restore /etc/ppp/option file and check if APN=unlimited username and  password are correct (ASK your provider). Also try setting 'Stupid mode = 1".

Retry and post results. Also post country, name of your provider and type of account (prepaid/contract).

Regards,
George


how to restore /etc/ppp/option file?

---

### Post by GeorgeVita on 2010-03-22
Correct filename: /etc/ppp/options
Attached filename: options.txt

Download attached file, copy it to Desktop, open a terminal:
```
sudo cp ~/Desktop/options.txt /etc/ppp/options
```

Good Luck,
G

---

### Post by fxlovers on 2010-03-22
report 

step 1
   
  cp ~/Desktop/options.txt /etc/ppp/options
   

step 2 
   
  xxx@xxx-laptop:~$ sudo wvdial mobi
  
  > 

--> WvDial: Internet dialer version 1.60
  
  --> Cannot get information for serial port.
  
  --> Initializing modem.
  
  --> Sending: ATZ
  
  ATZ
  
  ERROR
  
  --> Bad init string.
  
  --> Cannot get information for serial port.
  
  --> Initializing modem.
  
  --> Sending: ATZ
  
  ATZ
  
  OK
  
  --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
  
  ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
  
  OK
  
  ATZ E0 V1 X4 
  
  OK
  
  --> Modem initialized.
  
  --> Idle Seconds = 300, disabling automatic reconnect.
  
  --> Sending: ATDT#777
  
  --> Waiting for carrier.
  
  CONNECT 3100000
  
  --> Carrier detected.  Waiting for prompt.
  
  ~[7f]}#@!}!}"} }5}"}&} }*} } }#}%B#}%}%}&r!x@ej~
  
  --> PPP negotiation detected.
  
  --> Starting pppd at Tue Mar 23 01:49:54 2010
  
  --> Pid of pppd: 1998
  
  --> Using interface ppp0
  
  --> pppd: 0d:
  
  --> pppd: 0d:
  
  --> pppd: 0d:
  
  --> pppd: 0d:
  
  --> pppd: 0d:
  
  --> Disconnecting at Tue Mar 23 01:49:59 2010
  
  --> The PPP daemon has died: Authentication error.
  
  --> We failed to authenticate ourselves to the peer.
  
  --> Maybe bad account or password? (exit code = 19)
  
  --> man pppd explains pppd error codes in more detail.
  
  --> I guess that's it for now, exiting
  
  [FONT=&quot]--> The PPP daemon has died. (exit code = 19)
[/FONT][FONT=&quot]

[/FONT]step 3
   
  xxx@xxx-laptop:~$ sudo gedit /etc/ppp/pap-secrets
  xxx@xxx-laptop:~$ sudo gedit /etc/ppp/chap-secrets
   
   
  step 4 
   
  xxx@xxx-laptop:~$ sudo wvdial mobi
  
>     
  --> WvDial: Internet dialer version 1.60
  
  --> Cannot get information for serial port.
  
  --> Initializing modem.
  
  --> Sending: ATZ
  
  ~[7f]}#@!}!}!} }5}"}&} }*} } }#}%B#}%}%}&r$}+_i[08]~~[7f]}#@!}!}"} }5}"}&} }*} } }#}%B#}%}%}&r$}+_}"a~~[7f]}#@!}!}#} }5}"}&} }*} } }#}%B#}%}%}&r$}+_T>~~[7f]}#@!}!}$} }5}"}&} }*} } }#}%B#}%}%}&r$}+_T2~~[7f]}#@!}!}%} }5}"}&} }*} } }#}%B#}%}%}&r$}+_[02]m~~[7f]}#@!}!}&} }5}"}&} }*} } }#}%B#}%}%}&r$}+_i[04]~~[7f]}#@!}!}'} }5}"}&} }*} } }#}%B#}%}%}&r$}+_?[~~[7f]}#@!}!}(} }5}"}&} }*} } }#}%B#}%}%}&r$}+_i[1d]~~[7f]}#@!}!})} }5}"}&} }*} } }#}%B#}%}%}&r$}+_?B~~[7f]}#@!}!}*} }5}"}&} }*} } }#}%B#}%}%}&r$}+_T+~~[7f]}#@!}%}*} }$[1b]n~
  
  --> Sending: ATQ0
  
  --> Re-Sending: ATZ
  
  ~[7f]}#@!}!}!} }5}"}&} }*} } }#}%B#}%}%}&r$[1a][0e]hO~~[7f]}#@!}!}"} }5}"}&} }*} } }#}%B#}%}%}&r$[1a][0e][03]&~~[7f]}#@!}!}#} }5}"}&} }*} } }#}%B#}%}%}&r$[1a][0e]Uy~~[7f]}#@!}!}$} }5}"}&} }*} } }#}%B#}%}%}&r$[1a][0e]Uu~~[7f]}#@!}!}%} }5}"}&} }*} } }#}%B#}%}%}&r$[1a][0e]}#*~~[7f]}#@!}!}&} }5}"}&} }*} } }#}%B#}%}%}&r$[1a][0e]hC~~[7f]}#@!}!}'} }5}"}&} }*} } }#}%B#}%}%}&r$[1a][0e]>[1c]~~[7f]}#@!}!}(} }5}"}&} }*} } }#}%B#}%}%}&r$[1a][0e]hZ~~[7f]}#@!}!})} }5}"}&} }*} } }#}%B#}%}%}&r$[1a][0e]>[05]~~[7f]}#@!}!}*} }5}"}&} }*} } }#}%B#}%}%}&r$[1a][0e]Ul~~[7f]}#@!}%}*} }$[1b]n~
  
  [FONT=&quot]--> Modem not responding.[/FONT]  

step 5
   
  xxx@xxx-laptop:~$ sudo gedit /etc/ppp/peers/mobi

>   
  

   
  #
  
  #    /etc/ppp/peers/mobi
  
  #
  
  hide*password
  
  noauth
  
  connect '/usr/sbin/chat *v *f /etc/chatscripts/mobi'
  
  debug
  
  ttyUSB0
  
  921600
  
  defaultroute
  
  noipdefault
  
  user "my user name"
  
  remotename my user name

  ipparam my user name
  
  crtscts
  
  lock
  
  usepeerdns
   
  
step 6
   
  xxx@xxx-laptop:~$ sudo wvdial mobi

> 

  
  --> WvDial: Internet dialer version 1.60
  
  --> Cannot get information for serial port.
  
  --> Initializing modem.
  
  --> Sending: ATZ
  
  ~[7f]}#@!}!}!} }5}"}&} }*} } }#}%B#}%}%}&rI[xU|~~[7f]}#@!}!}"} }5}"}&} }*} } }#}%B#}%}%}&rI[x>[15]~~[7f]}#@!}!}#} }5}"}&} }*} } }#}%B#}%}%}&rI[xhJ~~[7f]}#@!}!}$} }5}"}&} }*} } }#}%B#}%}%}&rI[xhF~~[7f]}#@!}!}%} }5}"}&} }*} } }#}%B#}%}%}&rI[x>[19]~~[7f]}#@!}!}&} }5}"}&} }*} } }#}%B#}%}%}&rI[xUp~~[7f]}#@!}!}'} }5}"}&} }*} } }#}%B#}%}%}&rI[x[03]/~~[7f]}#@!}!}(} }5}"}&} }*} } }#}%B#}%}%}&rI[xUi~~[7f]}#@!}!})} }5}"}&} }*} } }#}%B#}%}%}&rI[x[03]6~~[7f]}#@!}!}*} }5}"}&} }*} } }#}%B#}%}%}&rI[xh_~~[7f]}#@!}%}*} }$[1b]n~
  
  --> Sending: ATQ0
  
  --> Re-Sending: ATZ
  
  ~[7f]}#@!}!}!} }5}"}&} }*} } }#}%B#}%}%}&rJi8c\~~[7f]}#@!}!}"} }5}"}&} }*} } }#}%B#}%}%}&rJi8}(5~~[7f]}#@!}!}#} }5}"}&} }*} } }#}%B#}%}%}&rJi8^j~~[7f]}#@!}!}$} }5}"}&} }*} } }#}%B#}%}%}&rJi8^f~~[7f]}#@!}!}%} }5}"}&} }*} } }#}%B#}%}%}&rJi8[08]9~~[7f]}#@!}!}&} }5}"}&} }*} } }#}%B#}%}%}&rJi8cP~~[7f]}#@!}!}'} }5}"}&} }*} } }#}%B#}%}%}&rJi85}/~~[7f]}#@!}!}(} }5}"}&} }*} } }#}%B#}%}%}&rJi8cI~~[7f]}#@!}!})} }5}"}&} }*} } }#}%B#}%}%}&rJi85}6~~[7f]}#@!}!}*} }5}"}&} }*} } }#}%B#}%}%}&rJi8^[7f]~~[7f]}#@!}%}*} }$[1b]n~
  
  --> Modem not responding.
  
  


---

### Post by GeorgeVita on 2010-03-22
... your 1st try is better! Do NOT change any file except /etc/wvdial.conf

REBOOT, read below and retry:

> ...**check if APN=unlimited username and password are correct** (ASK your provider). Also try setting 'Stupid mode = 1".
Retry and post results. **Also post country, name of your provider and type of account (prepaid/contract)**.

g

---

### Post by fxlovers on 2010-03-22
should i remove 

xxx@xxx-laptop:~$ sudo gedit /etc/ppp/pap-secrets
  xxx@xxx-laptop:~$ sudo gedit /etc/ppp/chap-secrets

how to remove?

---

### Post by fxlovers on 2010-03-22
still not responding


XXX@XXX-laptop:~$ sudo gedit /etc/wvdial.conf
  
> 
 [Dialer mobi]
  Init1 = ATZ
  Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
  Init3 = AT+CGDCONT=1,"IP"  <== my internet Provider not use APN

  Modem Type = Analog Modem
  ISDN = 0
  Phone = #777
  New PPPD = yes
  Modem = /dev/ttyUSB0
  Username = XXX
  Password = XXX
  Baud = 460800
  Carrier Check = no
  Ask Password = 0 
  Dial Command = ATDT 
  Stupid Mode = 1
  

   XXX@XXX-laptop:~$ sudo wvdial mobi
  
  
> 
    
  --> WvDial: Internet dialer version 1.60
  
  --> Cannot get information for serial port.
  
  --> Initializing modem.
  
  --> Sending: ATZ
  
  ~[7f]}#@!}!}!} }5}"}&} }*} } }#}%B#}%}%}&w}0-yB8~~[7f]}#@!}!}"} }5}"}&} }*} } }#}%B#}%}%}&w}0-y)Q~~[7f]}#@!}!}#} }5}"}&} }*} } }#}%B#}%}%}&w}0-y[7f]}.~~[7f]}#@!}!}$} }5}"}&} }*} } }#}%B#}%}%}&w}0-y[7f]}"~~[7f]}#@!}!}%} }5}"}&} }*} } }#}%B#}%}%}&w}0-y)]~~[7f]}#@!}!}&} }5}"}&} }*} } }#}%B#}%}%}&w}0-yB4~~[7f]}#@!}!}'} }5}"}&} }*} } }#}%B#}%}%}&w}0-y[14]k~~[7f]}#@!}!}(} }5}"}&} }*} } }#}%B#}%}%}&w}0-yB-~~[7f]}#@!}!})} }5}"}&} }*} } }#}%B#}%}%}&w}0-y[14]r~~[7f]}#@!}!}*} }5}"}&} }*} } }#}%B#}%}%}&w}0-y[7f]};~~[7f]}#@!}%}*} }$[1b]n~
  
  --> Sending: ATQ0
  
  --> Re-Sending: ATZ
  
  ~[7f]}#@!}!}!} }5}"}&} }*} } }#}%B#}%}%}&w}0;V2(~~[7f]}#@!}!}"} }5}"}&} }*} } }#}%B#}%}%}&w}0;VYA~~[7f]}#@!}!}#} }5}"}&} }*} } }#}%B#}%}%}&w}0;V[0f]}>~~[7f]}#@!}!}$} }5}"}&} }*} } }#}%B#}%}%}&w}0;V}/}2~~[7f]}#@!}!}%} }5}"}&} }*} } }#}%B#}%}%}&w}0;VYM~~[7f]}#@!}!}&} }5}"}&} }*} } }#}%B#}%}%}&w}0;V2$~~[7f]}#@!}!}'} }5}"}&} }*} } }#}%B#}%}%}&w}0;Vd{~~[7f]}#@!}!}(} }5}"}&} }*} } }#}%B#}%}%}&w}0;V2=~~[7f]}#@!}!})} }5}"}&} }*} } }#}%B#}%}%}&w}0;Vdb~~[7f]}#@!}!}*} }5}"}&} }*} } }#}%B#}%}%}&w}0;V}/}+~~[7f]}#@!}%}*} }$[1b]n~
  
  --> Modem not responding.

  


i try this :
 XXX@XXX-laptop:~$ [FONT=&quot]sudo gedit /etc/ppp/peers/mobi[/FONT]
  
> 

   #
  #    /etc/ppp/peers/mobi
  #
  hide*password
  noauth
  connect '/usr/sbin/chat *v *f /etc/chatscripts/mobi'
  debug
  ttyUSB0
  921600
  defaultroute
  noipdefault
  user "08891492122@unlimited"
  remotename
  ipparam 
  crtscts
  lock
  usepeerdns



    [FONT=&quot]XXX@XXX-laptop:~$ sudo wvdial mobi[/FONT]

[FONT=&quot][/FONT]
[FONT=&quot]> [/FONT]
    --> WvDial: Internet dialer version 1.60
  
  --> Cannot get information for serial port.
  
  --> Initializing modem.
  
  --> Sending: ATZ
  
  ~[7f]}#@!}!}!} }5}"}&} }*} } }#}%B#}%}%}&w}4dWe
  
  ~~[7f]}#@!}!}"} }5}"}&} }*} } }#}%B#}%}%}&w}4dW}.c~~[7f]}#@!}!}#} }5}"}&} }*} } }#}%B#}%}%}&w}4dWX<~~[7f]}#@!}!}$} }5}"}&} }*} } }#}%B#}%}%}&w}4dWX0~~[7f]}#@!}!}%} }5}"}&} }*} } }#}%B#}%}%}&w}4dW[0e]o~~[7f]}#@!}!}&} }5}"}&} }*} } }#}%B#}%}%}&w}4dWe[06]~~[7f]}#@!}!}'} }5}"}&} }*} } }#}%B#}%}%}&w}4dW3Y~~[7f]}#@!}!}(} }5}"}&} }*} } }#}%B#}%}%}&w}4dWe[1f]~~[7f]}#@!}!})} }5}"}&} }*} } }#}%B#}%}%}&w}4dW3@~~[7f]}#@!}!}*} }5}"}&} }*} } }#}%B#}%}%}&w}4dWX)~~[7f]}#@!}%}*} }$[1b]n~
  
  --> Sending: ATQ0
  
  --> Re-Sending: ATZ
  
  ~[7f]}#@!}!}!} }5}"}&} }*} } }#}%B#}%}%}&w}5pq8n~~[7f]}#@!}!}"} }5}"}&} }*} } }#}%B#}%}%}&w}5pqS}'~~[7f]}#@!}!}#} }5}"}&} }*} } }#}%B#}%}%}&w}5pq[05]X~~[7f]}#@!}!}$} }5}"}&} }*} } }#}%B#}%}%}&w}5pq}%T~~[7f]}#@!}!}%} }5}"}&} }*} } }#}%B#}%}%}&w}5pqS}+~~[7f]}#@!}!}&} }5}"}&} }*} } }#}%B#}%}%}&w}5pq8b~~[7f]}#@!}!}'} }5}"}&} }*} } }#}%B#}%}%}&w}5pqn=~~[7f]}#@!}!}(} }5}"}&} }*} } }#}%B#}%}%}&w}5pq8{~~[7f]}#@!}!})} }5}"}&} }*} } }#}%B#}%}%}&w}5pqn$~~[7f]}#@!}!}*} }5}"}&} }*} } }#}%B#}%}%}&w}5pq}%M~~[7f]}#@!}%}*} }$[1b]n~
  
  --> Modem not responding.
  

  

---

### Post by pdc on 2010-03-23
do you have access to the internet from another source?

I would suggest you download a version of Ubuntu 9.04 and run as a liveCD and see if you get any joy;

or any older version of any linux distro that you or a friend may have around

also:

what does 

> lsusb

in a terminal give? That would help us identify the hardware

---

### Post by fxlovers on 2010-03-25
done...
thanks for the help.... i can connect the internet thru my ubuntu
--------------------------------------
i just re-install my ubuntu. 
install usb-modemswitch
install wvdial
---------------------------------------
this post is using my ubuntu 9.10...

:guitar:

---

### Post by pdc on 2010-03-26
great! well done!

.......... if you're still there!!

...if you can spell out the details of what you did,..... others may well want to use this modem ....

did usb_modeswitch auto-configure for you (as it should ..)

did you use the wvdial.conf you quoted?

and give us 

> lsusb

so we know what modem it is and can you give

> dmesg grep | ttyUSB

with the modem plugged in

---

### Post by fxlovers on 2010-03-26
posted...
how to connect to the Internet using a usb modem 

[http://ubuntuforums.org/showthread.php?p=9030540#post9030540](http://ubuntuforums.org/showthread.php?p=9030540#post9030540)

---

