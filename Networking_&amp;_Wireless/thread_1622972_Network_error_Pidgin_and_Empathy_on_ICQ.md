---
title: "Network error Pidgin and Empathy on ICQ"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by Orange Kingdom on 2010-11-16
Hi,
Since 2 days i cannot login with  Pidgin and Empathy on icq.
MSN is working,icq not.

I get "network error" .


My internet connection is ok.

I have the newest versions installed.


Any idea?

---

### Post by yarozar on 2010-11-16
I confirm- "Network error" for ICQ - have the very same issue starting today (16th Nov). Yesterday (15th Nov) everything was ok.

At the same time jabber, yahoo and google accounts work as always.

---

### Post by apoapo on 2010-11-16
Exactly the same here. Pidgin works

---

### Post by scr3amingeagle on 2010-11-16
samething happening here.  everything else is working but icq.

---

### Post by julianibus on 2010-11-16
Same problem. No empathy. No Pidgin.

---

### Post by redusek on 2010-11-16
I've heard that changing your server to login.icq.com will help.  I've done that, though, and it has not helped.

---

### Post by Speeder_nl on 2010-11-16
Hi, it seems that the protocol or something else changed on the server side of AIM/ICQ. For Pidgin you can change the url to login.icq.com and remove the check for ssl. Too bad there is no option for this in empathy, I like it when I am in control of an application in stead of the programmer or the OS.

---

### Post by ar_victor on 2010-11-16
Ubuntu: 10.04
Pidgin: 2.6.6
(libpurple 2.6.6)

On ICQ Account, choose 'Advanced' tab & check 'Use clientLogin'. It works for me. ICQ is alive!

---

### Post by VinDSL on 2010-11-16
If you absolutely, positively, need to use ICQ...

Launch ICQ2go (Web ICQ) in a browser window:  [http://www.icq.com/download/webicq/](http://www.icq.com/download/webicq/)

This URL is handy, when you're on the trot, at work, on a public library terminal, et cetera...

Works every time!  ;)

---

### Post by julianibus on 2010-11-16
I got it working:
Server: login.icq.com
SSL: off

---

### Post by spiregrain on 2010-11-16
Thanks for this.  I'm not seeing an SSL option in Empathy - only UIN, Password, Character set, Server and Port.  Where is it?

---

### Post by julianibus on 2010-11-16
In Pidgin there's an SSL Option. Im don't know how to fix that in empathy.

---

### Post by Orange Kingdom on 2010-11-17
works again with ssl off and login.icq.com

Thanks!

---

### Post by sabotatore on 2010-11-17
So what to do with emphaty?

---

### Post by haeuslein on 2010-11-17
I have the same problem. In pidgin you can simply turn off SSL and it will work. How do you turn off SSL in Empathy?

---

### Post by change_mode on 2010-11-17
Disabling SSL is a pretty bad idea, so both clients should probably be fixed asap.

---

### Post by Stoneface on 2010-11-18
Cannot connect to ICQ using Empathy anymore either. Using Empathy 2.32.0.1 on Maverick Meerkat. Tried login.icq.com with port 4000 and 5190. Nu luck. Wonder how to fix this and where to read the ICQ error logs. Did find debug log, but did not see real errors or something useful:
```
mcd-DEBUG: 11/18/2010 08:08:45.600728: presence_get_statuses_cb:   available
mcd-DEBUG: 11/18/2010 08:08:45.600728: presence_get_statuses_cb:   hidden
mcd-DEBUG: 11/18/2010 08:08:45.600728: presence_get_statuses_cb:   offline
mcd-DEBUG: 11/18/2010 08:08:45.600728: _mcd_connection_set_presence: Setting status 'available' of type 2 ('available' was requested)
mcd-DEBUG: 11/18/2010 08:08:45.600779: _mcd_dispatcher_add_connection: 0x879a4a0: 0x879cd58 (/org/freedesktop/Telepathy/Connection/haze/icq/_3568211595)
mcd-DEBUG: 11/18/2010 08:08:45.600862: _mcd_connection_start_dispatching: 0x879cd58
mcd-DEBUG: 11/18/2010 08:08:45.601118: _mcd_connection_update_client_caps: ContactCapabilities unsupported
mcd-DEBUG: 11/18/2010 08:08:45.601186: mcd_connection_done_task_before_connect: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Calling Connect()
mcd-DEBUG: 11/18/2010 08:08:45.605334: on_connection_status_changed: status_changed called from tp (1)
mcd-DEBUG: 11/18/2010 08:08:45.605353: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:08:45.605357: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:08:45.605369: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:08:45.605374: mcd_account_changed_property: Forcibly emit PropertiesChanged now
mcd-DEBUG: 11/18/2010 08:08:45.605377: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:08:45.608217: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:08:45.612782: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:08:45.612798: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:08:45.612808: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:08:45.612833: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:08:45.612849: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:08:45.612854: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:08:45.665112: connect_cb: called for connection 0x879cd58
mcd-DEBUG: 11/18/2010 08:08:48.282583: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:08:48.282583: mcd_connection_invalidated_cb: Proxy destroyed (Network error)!
mcd-DEBUG: 11/18/2010 08:08:48.282583: _mcd_connection_release_tp_connection: 0x879cd58
mcd-DEBUG: 11/18/2010 08:08:48.282618: _mcd_account_set_connection_status: haze/icq/_35682115950: 2 because 2
mcd-DEBUG: 11/18/2010 08:08:48.282623: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:08:48.282629: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 11/18/2010 08:08:48.282634: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 11/18/2010 08:08:48.282643: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:08:48.282648: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:08:48.282890: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:08:48.282890: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:08:48.282890: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:08:48.282896: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:08:48.282917: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:08:48.282921: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:08:48.283112: mcd_connection_invalidated_cb: Preparing for reconnection in 9 seconds
mcd-DEBUG: 11/18/2010 08:08:48.283124: on_connection_ready: got error: Network error
mcd-DEBUG: 11/18/2010 08:08:57.578931: mcd_connection_reconnect: 0x879cd58
mcd-DEBUG: 11/18/2010 08:08:57.578965: _mcd_connection_attempt: called for 0x879cd58, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:08:57.578983: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:08:57.579051: _mcd_connection_connect: called for 0x879cd58, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:08:57.579061: _mcd_connection_connect_with_params: Trying connect account: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:08:57.579078: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:08:57.579083: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:08:57.579088: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 11/18/2010 08:08:57.579092: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 11/18/2010 08:08:57.579102: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:08:57.579107: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:08:57.579257: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:08:57.579265: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:08:57.579272: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:08:57.579302: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:08:57.579315: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:08:57.579320: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:08:57.893882: request_connection_cb: created /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595
mcd-DEBUG: 11/18/2010 08:08:57.894416: _mcd_connection_set_tp_connection: new connection is 0x87c1bc0
mcd-DEBUG: 11/18/2010 08:08:57.894428: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:08:57.894433: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:08:57.895353: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:08:57.897217: mcd_connection_early_get_statuses_cb: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Early Get(Statuses) succeeded
mcd-DEBUG: 11/18/2010 08:08:57.897226: presence_get_statuses_cb: account haze/icq/_35682115950:
mcd-DEBUG: 11/18/2010 08:08:57.897226: presence_get_statuses_cb:   busy
mcd-DEBUG: 11/18/2010 08:08:57.897226: presence_get_statuses_cb:   away
mcd-DEBUG: 11/18/2010 08:08:57.897226: presence_get_statuses_cb:   xa
mcd-DEBUG: 11/18/2010 08:08:57.897226: presence_get_statuses_cb:   available
mcd-DEBUG: 11/18/2010 08:08:57.897226: presence_get_statuses_cb:   hidden
mcd-DEBUG: 11/18/2010 08:08:57.897226: presence_get_statuses_cb:   offline
mcd-DEBUG: 11/18/2010 08:08:57.897226: _mcd_connection_set_presence: Setting status 'available' of type 2 ('available' was requested)
mcd-DEBUG: 11/18/2010 08:08:57.897310: _mcd_dispatcher_add_connection: 0x879a4a0: 0x879cd58 (/org/freedesktop/Telepathy/Connection/haze/icq/_3568211595)
mcd-DEBUG: 11/18/2010 08:08:57.897372: _mcd_connection_start_dispatching: 0x879cd58
mcd-DEBUG: 11/18/2010 08:08:57.897629: _mcd_connection_update_client_caps: ContactCapabilities unsupported
mcd-DEBUG: 11/18/2010 08:08:57.897690: mcd_connection_done_task_before_connect: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Calling Connect()
mcd-DEBUG: 11/18/2010 08:08:57.899763: on_connection_status_changed: status_changed called from tp (1)
mcd-DEBUG: 11/18/2010 08:08:57.899777: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:08:57.899782: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:08:57.899791: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:08:57.899795: mcd_account_changed_property: Forcibly emit PropertiesChanged now
mcd-DEBUG: 11/18/2010 08:08:57.899799: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:08:57.899892: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:08:57.900021: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:08:57.900032: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:08:57.900044: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:08:57.900059: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:08:57.900073: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:08:57.900078: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:08:57.988162: connect_cb: called for connection 0x879cd58
mcd-DEBUG: 11/18/2010 08:09:00.678879: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:09:00.678972: mcd_connection_invalidated_cb: Proxy destroyed (Network error)!
mcd-DEBUG: 11/18/2010 08:09:00.678980: _mcd_connection_release_tp_connection: 0x879cd58
mcd-DEBUG: 11/18/2010 08:09:00.678991: _mcd_account_set_connection_status: haze/icq/_35682115950: 2 because 2
mcd-DEBUG: 11/18/2010 08:09:00.678991: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:09:00.678991: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 11/18/2010 08:09:00.678991: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 11/18/2010 08:09:00.678991: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:09:00.678992: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:09:00.679408: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:09:00.679415: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:09:00.679424: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:09:00.679449: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:09:00.679464: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:09:00.679469: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:09:00.679666: mcd_connection_invalidated_cb: Preparing for reconnection in 27 seconds
mcd-DEBUG: 11/18/2010 08:09:00.679678: on_connection_ready: got error: Network error
mcd-DEBUG: 11/18/2010 08:09:27.579202: mcd_connection_reconnect: 0x879cd58
mcd-DEBUG: 11/18/2010 08:09:27.579241: _mcd_connection_attempt: called for 0x879cd58, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:09:27.579260: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:09:27.579324: _mcd_connection_connect: called for 0x879cd58, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:09:27.579336: _mcd_connection_connect_with_params: Trying connect account: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:09:27.579360: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:09:27.579365: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:09:27.579370: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 11/18/2010 08:09:27.579375: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 11/18/2010 08:09:27.579385: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:09:27.579391: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:09:27.579854: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:09:27.579865: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:09:27.579879: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:09:27.579907: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:09:27.579922: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:09:27.579927: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:09:27.804780: request_connection_cb: created /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595
mcd-DEBUG: 11/18/2010 08:09:27.805210: _mcd_connection_set_tp_connection: new connection is 0x87c1c40
mcd-DEBUG: 11/18/2010 08:09:27.805222: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:09:27.805227: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:09:27.806169: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:09:27.807977: mcd_connection_early_get_statuses_cb: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Early Get(Statuses) succeeded
mcd-DEBUG: 11/18/2010 08:09:27.807986: presence_get_statuses_cb: account haze/icq/_35682115950:
mcd-DEBUG: 11/18/2010 08:09:27.807995: presence_get_statuses_cb:   busy
mcd-DEBUG: 11/18/2010 08:09:27.808000: presence_get_statuses_cb:   away
mcd-DEBUG: 11/18/2010 08:09:27.808003: presence_get_statuses_cb:   xa
mcd-DEBUG: 11/18/2010 08:09:27.808008: presence_get_statuses_cb:   available
mcd-DEBUG: 11/18/2010 08:09:27.808012: presence_get_statuses_cb:   hidden
mcd-DEBUG: 11/18/2010 08:09:27.808017: presence_get_statuses_cb:   offline
mcd-DEBUG: 11/18/2010 08:09:27.808026: _mcd_connection_set_presence: Setting status 'available' of type 2 ('available' was requested)
mcd-DEBUG: 11/18/2010 08:09:27.808064: _mcd_dispatcher_add_connection: 0x879a4a0: 0x879cd58 (/org/freedesktop/Telepathy/Connection/haze/icq/_3568211595)
mcd-DEBUG: 11/18/2010 08:09:27.808140: _mcd_connection_start_dispatching: 0x879cd58
mcd-DEBUG: 11/18/2010 08:09:27.808274: _mcd_connection_update_client_caps: ContactCapabilities unsupported
mcd-DEBUG: 11/18/2010 08:09:27.808347: mcd_connection_done_task_before_connect: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Calling Connect()
mcd-DEBUG: 11/18/2010 08:09:27.810771: on_connection_status_changed: status_changed called from tp (1)
mcd-DEBUG: 11/18/2010 08:09:27.810771: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:09:27.810771: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:09:27.810771: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:09:27.810771: mcd_account_changed_property: Forcibly emit PropertiesChanged now
mcd-DEBUG: 11/18/2010 08:09:27.810771: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:09:27.810811: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:09:27.811009: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:09:27.811017: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:09:27.811024: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:09:27.811039: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:09:27.811053: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:09:27.811058: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:09:27.868629: connect_cb: called for connection 0x879cd58
mcd-DEBUG: 11/18/2010 08:09:30.453782: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:09:30.453870: mcd_connection_invalidated_cb: Proxy destroyed (Network error)!
mcd-DEBUG: 11/18/2010 08:09:30.453876: _mcd_connection_release_tp_connection: 0x879cd58
mcd-DEBUG: 11/18/2010 08:09:30.453887: _mcd_account_set_connection_status: haze/icq/_35682115950: 2 because 2
mcd-DEBUG: 11/18/2010 08:09:30.453887: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:09:30.453887: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 11/18/2010 08:09:30.453887: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 11/18/2010 08:09:30.453887: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:09:30.453888: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:09:30.454163: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:09:30.454163: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:09:30.454163: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:09:30.454168: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:09:30.454189: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:09:30.454194: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:09:30.454385: mcd_connection_invalidated_cb: Preparing for reconnection in 81 seconds
mcd-DEBUG: 11/18/2010 08:09:30.454399: on_connection_ready: got error: Network error
mcd-DEBUG: 11/18/2010 08:10:51.652622: mcd_connection_reconnect: 0x879cd58
mcd-DEBUG: 11/18/2010 08:10:51.652674: _mcd_connection_attempt: called for 0x879cd58, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:10:51.652693: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:10:51.652775: _mcd_connection_connect: called for 0x879cd58, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:10:51.652781: _mcd_connection_connect_with_params: Trying connect account: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:10:51.652803: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:10:51.652807: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:10:51.652815: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 11/18/2010 08:10:51.652820: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 11/18/2010 08:10:51.652831: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:10:51.652836: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:10:51.653110: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:10:51.653126: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:10:51.653135: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:10:51.653163: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:10:51.653178: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:10:51.653184: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:10:51.863095: request_connection_cb: created /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595
mcd-DEBUG: 11/18/2010 08:10:51.863701: _mcd_connection_set_tp_connection: new connection is 0x87c1cc0
mcd-DEBUG: 11/18/2010 08:10:51.863713: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:10:51.863718: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:10:51.864496: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:10:51.866303: mcd_connection_early_get_statuses_cb: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Early Get(Statuses) succeeded
mcd-DEBUG: 11/18/2010 08:10:51.866313: presence_get_statuses_cb: account haze/icq/_35682115950:
mcd-DEBUG: 11/18/2010 08:10:51.866321: presence_get_statuses_cb:   busy
mcd-DEBUG: 11/18/2010 08:10:51.866326: presence_get_statuses_cb:   away
mcd-DEBUG: 11/18/2010 08:10:51.866331: presence_get_statuses_cb:   xa
mcd-DEBUG: 11/18/2010 08:10:51.866334: presence_get_statuses_cb:   available
mcd-DEBUG: 11/18/2010 08:10:51.866339: presence_get_statuses_cb:   hidden
mcd-DEBUG: 11/18/2010 08:10:51.866344: presence_get_statuses_cb:   offline
mcd-DEBUG: 11/18/2010 08:10:51.866353: _mcd_connection_set_presence: Setting status 'available' of type 2 ('available' was requested)
mcd-DEBUG: 11/18/2010 08:10:51.866606: _mcd_dispatcher_add_connection: 0x879a4a0: 0x879cd58 (/org/freedesktop/Telepathy/Connection/haze/icq/_3568211595)
mcd-DEBUG: 11/18/2010 08:10:51.866719: _mcd_connection_start_dispatching: 0x879cd58
mcd-DEBUG: 11/18/2010 08:10:51.866770: _mcd_connection_update_client_caps: ContactCapabilities unsupported
mcd-DEBUG: 11/18/2010 08:10:51.866770: mcd_connection_done_task_before_connect: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Calling Connect()
mcd-DEBUG: 11/18/2010 08:10:51.868807: on_connection_status_changed: status_changed called from tp (1)
mcd-DEBUG: 11/18/2010 08:10:51.868822: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:10:51.868827: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:10:51.868835: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:10:51.868840: mcd_account_changed_property: Forcibly emit PropertiesChanged now
mcd-DEBUG: 11/18/2010 08:10:51.868845: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:10:51.868937: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:10:51.869033: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:10:51.869033: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:10:51.869033: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:10:51.869041: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:10:51.869062: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:10:51.869066: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:10:51.924357: connect_cb: called for connection 0x879cd58
mcd-DEBUG: 11/18/2010 08:10:54.739806: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:10:54.739901: mcd_connection_invalidated_cb: Proxy destroyed (Network error)!
mcd-DEBUG: 11/18/2010 08:10:54.739908: _mcd_connection_release_tp_connection: 0x879cd58
mcd-DEBUG: 11/18/2010 08:10:54.739922: _mcd_account_set_connection_status: haze/icq/_35682115950: 2 because 2
mcd-DEBUG: 11/18/2010 08:10:54.739922: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:10:54.739922: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 11/18/2010 08:10:54.739922: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 11/18/2010 08:10:54.739922: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:10:54.739922: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:10:54.740256: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:10:54.740256: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:10:54.740256: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:10:54.740256: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:10:54.740262: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:10:54.740273: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:10:54.740500: mcd_connection_invalidated_cb: Preparing for reconnection in 243 seconds
mcd-DEBUG: 11/18/2010 08:10:54.740521: on_connection_ready: got error: Network error
mcd-DEBUG: 11/18/2010 08:11:09.743884: account_update_parameters: called for haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:09.743894: _mcd_account_set_parameters: called
mcd-DEBUG: 11/18/2010 08:11:09.744219: update_storage: MCP:default-gkeyfile -> store haze/icq/_35682115950.param-server
mcd-DEBUG: 11/18/2010 08:11:09.744227: mcd_account_check_parameters: called for haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:09.744263: _mcd_account_maybe_autoconnect: haze/icq/_35682115950 does not ConnectAutomatically
mcd-DEBUG: 11/18/2010 08:11:09.744276: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:11:09.744337: mcd_account_changed_property: called: Parameters
mcd-DEBUG: 11/18/2010 08:11:09.744342: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:09.744378: _storage_commit: flushing plugin default-gkeyfile haze/icq/_35682115950 to long term storage
mcd-DEBUG: 11/18/2010 08:11:09.744400: _have_config: checking for /home/jasper/.mission-control/accounts/accounts.cfg
mc-plugins-DEBUG: 11/18/2010 08:11:09.744178: mcp_account_storage_set: default-gkeyfile: 
mc-plugins-DEBUG: 11/18/2010 08:11:09.744400: mcp_account_storage_commit_one: default-gkeyfile: 
mcd-DEBUG: 11/18/2010 08:11:09.783605: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:09.791157: account_reconnect: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:09.791157: _mcd_connection_release_tp_connection: 0x879cd58
mcd-DEBUG: 11/18/2010 08:11:09.791163: _mcd_account_set_connection_status: haze/icq/_35682115950: 2 because 1
mcd-DEBUG: 11/18/2010 08:11:09.791174: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:09.791183: _mcd_account_set_connection_status: changing detailed D-Bus error from 'org.freedesktop.Telepathy.Error.NetworkError' to ''
mcd-DEBUG: 11/18/2010 08:11:09.791191: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 11/18/2010 08:11:09.791199: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:09.791204: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:09.791349: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:11:09.791359: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:11:09.791367: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:11:09.791385: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:11:09.791402: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:09.791407: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:09.791594: _mcd_operation_abort: Operation abort received, aborting all children
mcd-DEBUG: 11/18/2010 08:11:09.791605: on_connection_abort: called (0x879cd58, account haze/icq/_35682115950)
mcd-DEBUG: 11/18/2010 08:11:09.791631: _mcd_mission_set_parent: child = 0x879cd58, parent = (nil)
mcd-DEBUG: 11/18/2010 08:11:09.791646: _mcd_operation_remove_mission: removing mission: 0x879cd58
mcd-DEBUG: 11/18/2010 08:11:09.791656: _mcd_connection_dispose: called for object 0x879cd58
mcd-DEBUG: 11/18/2010 08:11:09.791665: _mcd_connection_release_tp_connection: 0x879cd58
mcd-DEBUG: 11/18/2010 08:11:09.791680: _mcd_operation_dispose: operation disposed
mcd-DEBUG: 11/18/2010 08:11:09.791687: _mcd_mission_dispose: mission disposed 0x879cd58
mcd-DEBUG: 11/18/2010 08:11:09.791687: mcd_dispatcher_lost_connection: 0x879a4a0: 0x879cd58
mcd-DEBUG: 11/18/2010 08:11:09.791687: mcd_dispatcher_lost_connection: 0x879a4a0: 0x879cd58
mcd-DEBUG: 11/18/2010 08:11:09.791687: mcd_dispatcher_lost_connection: 0x879a4a0: 0x879cd58
mcd-DEBUG: 11/18/2010 08:11:09.791687: mcd_dispatcher_lost_connection: 0x879a4a0: 0x879cd58
mcd-DEBUG: 11/18/2010 08:11:09.791687: mcd_dispatcher_lost_connection: 0x879a4a0: 0x879cd58
mcd-DEBUG: 11/18/2010 08:11:09.791687: _mcd_mission_finalize: mission finalized 0x879cd58
mcd-DEBUG: 11/18/2010 08:11:09.791687: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:11:09.791687: _mcd_mission_set_parent: child = 0x879cdc0, parent = 0x87a7060
mcd-DEBUG: 11/18/2010 08:11:09.791687: mcd_manager_create_connection: Created a connection 0x879cdc0 for account: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:09.791687: _mcd_connection_connect: called for 0x879cdc0, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:09.791687: _mcd_connection_connect_with_params: Trying connect account: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:09.791687: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:11:09.791687: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:09.791687: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 11/18/2010 08:11:09.791687: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:09.791687: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:09.791688: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:11:09.791688: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:11:09.791688: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:11:09.791688: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:11:09.791688: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:09.791690: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:10.6650: _keyring_set_cb: saved haze/icq/_35682115950.param-password in gnome keyring
mcd-DEBUG: 11/18/2010 08:11:10.43221: request_connection_cb: created /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595
mcd-DEBUG: 11/18/2010 08:11:10.43637: _mcd_connection_set_tp_connection: new connection is 0x87c1d40
mcd-DEBUG: 11/18/2010 08:11:10.43651: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:10.43657: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:10.44584: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:11:10.46195: mcd_connection_early_get_statuses_cb: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Early Get(Statuses) succeeded
mcd-DEBUG: 11/18/2010 08:11:10.46219: presence_get_statuses_cb: account haze/icq/_35682115950:
mcd-DEBUG: 11/18/2010 08:11:10.46227: presence_get_statuses_cb:   busy
mcd-DEBUG: 11/18/2010 08:11:10.46233: presence_get_statuses_cb:   away
mcd-DEBUG: 11/18/2010 08:11:10.46238: presence_get_statuses_cb:   xa
mcd-DEBUG: 11/18/2010 08:11:10.46242: presence_get_statuses_cb:   available
mcd-DEBUG: 11/18/2010 08:11:10.46247: presence_get_statuses_cb:   hidden
mcd-DEBUG: 11/18/2010 08:11:10.46252: presence_get_statuses_cb:   offline
mcd-DEBUG: 11/18/2010 08:11:10.46262: _mcd_connection_set_presence: Setting status 'available' of type 2 ('available' was requested)
mcd-DEBUG: 11/18/2010 08:11:10.46510: _mcd_dispatcher_add_connection: 0x879a4a0: 0x879cdc0 (/org/freedesktop/Telepathy/Connection/haze/icq/_3568211595)
mcd-DEBUG: 11/18/2010 08:11:10.46583: _mcd_connection_start_dispatching: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:11:10.46583: _mcd_connection_update_client_caps: ContactCapabilities unsupported
mcd-DEBUG: 11/18/2010 08:11:10.46583: mcd_connection_done_task_before_connect: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Calling Connect()
mcd-DEBUG: 11/18/2010 08:11:10.51515: on_connection_status_changed: status_changed called from tp (1)
mcd-DEBUG: 11/18/2010 08:11:10.51531: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:11:10.51536: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:10.51546: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:10.51551: mcd_account_changed_property: Forcibly emit PropertiesChanged now
mcd-DEBUG: 11/18/2010 08:11:10.51556: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:10.51650: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:10.51794: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:11:10.51794: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:11:10.51794: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:11:10.51794: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:11:10.51794: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:10.51794: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:10.116487: connect_cb: called for connection 0x879cdc0
mcd-DEBUG: 11/18/2010 08:11:12.890012: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:11:12.890132: mcd_connection_invalidated_cb: Proxy destroyed (Network error)!
mcd-DEBUG: 11/18/2010 08:11:12.890141: _mcd_connection_release_tp_connection: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:11:12.890152: _mcd_account_set_connection_status: haze/icq/_35682115950: 2 because 2
mcd-DEBUG: 11/18/2010 08:11:12.890152: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:12.890152: _mcd_account_set_connection_status: changing detailed D-Bus error from '' to 'org.freedesktop.Telepathy.Error.NetworkError'
mcd-DEBUG: 11/18/2010 08:11:12.890152: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 11/18/2010 08:11:12.890152: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 11/18/2010 08:11:12.890152: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:12.890152: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:12.890376: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:11:12.890391: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:11:12.890399: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:11:12.890424: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:11:12.890440: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:12.890446: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:12.890635: mcd_connection_invalidated_cb: Preparing for reconnection in 3 seconds
mcd-DEBUG: 11/18/2010 08:11:12.890650: on_connection_ready: got error: Network error
mcd-DEBUG: 11/18/2010 08:11:16.579025: mcd_connection_reconnect: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:11:16.579045: _mcd_connection_attempt: called for 0x879cdc0, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:16.579057: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:11:16.579224: _mcd_connection_connect: called for 0x879cdc0, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:16.579231: _mcd_connection_connect_with_params: Trying connect account: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:16.579246: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:11:16.579252: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:16.579257: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 11/18/2010 08:11:16.579263: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 11/18/2010 08:11:16.579276: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:16.579281: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:16.579499: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:11:16.579508: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:11:16.579514: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:11:16.579543: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:11:16.579559: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:16.579564: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:16.597615: request_connection_cb: created /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595
mcd-DEBUG: 11/18/2010 08:11:16.599086: _mcd_connection_set_tp_connection: new connection is 0x87c1dc0
mcd-DEBUG: 11/18/2010 08:11:16.599100: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:16.599106: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:16.600699: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:11:16.604809: mcd_connection_early_get_statuses_cb: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Early Get(Statuses) succeeded
mcd-DEBUG: 11/18/2010 08:11:16.604823: presence_get_statuses_cb: account haze/icq/_35682115950:
mcd-DEBUG: 11/18/2010 08:11:16.604824: presence_get_statuses_cb:   busy
mcd-DEBUG: 11/18/2010 08:11:16.604824: presence_get_statuses_cb:   away
mcd-DEBUG: 11/18/2010 08:11:16.604824: presence_get_statuses_cb:   xa
mcd-DEBUG: 11/18/2010 08:11:16.604824: presence_get_statuses_cb:   available
mcd-DEBUG: 11/18/2010 08:11:16.604824: presence_get_statuses_cb:   hidden
mcd-DEBUG: 11/18/2010 08:11:16.604824: presence_get_statuses_cb:   offline
mcd-DEBUG: 11/18/2010 08:11:16.604824: _mcd_connection_set_presence: Setting status 'available' of type 2 ('available' was requested)
mcd-DEBUG: 11/18/2010 08:11:16.604824: _mcd_dispatcher_add_connection: 0x879a4a0: 0x879cdc0 (/org/freedesktop/Telepathy/Connection/haze/icq/_3568211595)
mcd-DEBUG: 11/18/2010 08:11:16.604824: _mcd_connection_start_dispatching: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:11:16.604897: _mcd_connection_update_client_caps: ContactCapabilities unsupported
mcd-DEBUG: 11/18/2010 08:11:16.604963: mcd_connection_done_task_before_connect: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Calling Connect()
mcd-DEBUG: 11/18/2010 08:11:16.612222: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:16.616688: on_connection_status_changed: status_changed called from tp (1)
mcd-DEBUG: 11/18/2010 08:11:16.616688: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:11:16.616688: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:16.616688: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:16.616688: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:16.616688: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:11:16.616688: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:11:16.616688: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:11:16.616688: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:11:16.616688: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:16.616688: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:16.685219: connect_cb: called for connection 0x879cdc0
mcd-DEBUG: 11/18/2010 08:11:19.111345: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:11:19.111407: mcd_connection_invalidated_cb: Proxy destroyed (Network error)!
mcd-DEBUG: 11/18/2010 08:11:19.111422: _mcd_connection_release_tp_connection: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:11:19.111452: _mcd_account_set_connection_status: haze/icq/_35682115950: 2 because 2
mcd-DEBUG: 11/18/2010 08:11:19.111459: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:19.111466: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 11/18/2010 08:11:19.111473: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 11/18/2010 08:11:19.111483: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:19.111488: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:19.111761: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:11:19.111776: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:11:19.111784: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:11:19.111809: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:11:19.111825: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:19.111831: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:19.112020: mcd_connection_invalidated_cb: Preparing for reconnection in 9 seconds
mcd-DEBUG: 11/18/2010 08:11:19.112035: on_connection_ready: got error: Network error
mcd-DEBUG: 11/18/2010 08:11:28.578838: mcd_connection_reconnect: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:11:28.578872: _mcd_connection_attempt: called for 0x879cdc0, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:28.578933: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:11:28.579111: _mcd_connection_connect: called for 0x879cdc0, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:28.579117: _mcd_connection_connect_with_params: Trying connect account: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:28.579138: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:11:28.579143: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:28.579150: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 11/18/2010 08:11:28.579157: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 11/18/2010 08:11:28.579165: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:28.579171: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:28.579483: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:11:28.579498: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:11:28.579504: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:11:28.579534: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:11:28.579550: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:28.579555: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:28.799540: request_connection_cb: created /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595
mcd-DEBUG: 11/18/2010 08:11:28.799967: _mcd_connection_set_tp_connection: new connection is 0x87c1dc0
mcd-DEBUG: 11/18/2010 08:11:28.799978: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:28.799985: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:28.800832: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:11:28.804424: mcd_connection_early_get_statuses_cb: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Early Get(Statuses) succeeded
mcd-DEBUG: 11/18/2010 08:11:28.804434: presence_get_statuses_cb: account haze/icq/_35682115950:
mcd-DEBUG: 11/18/2010 08:11:28.804441: presence_get_statuses_cb:   busy
mcd-DEBUG: 11/18/2010 08:11:28.804447: presence_get_statuses_cb:   away
mcd-DEBUG: 11/18/2010 08:11:28.804452: presence_get_statuses_cb:   xa
mcd-DEBUG: 11/18/2010 08:11:28.804457: presence_get_statuses_cb:   available
mcd-DEBUG: 11/18/2010 08:11:28.804464: presence_get_statuses_cb:   hidden
mcd-DEBUG: 11/18/2010 08:11:28.804469: presence_get_statuses_cb:   offline
mcd-DEBUG: 11/18/2010 08:11:28.804478: _mcd_connection_set_presence: Setting status 'available' of type 2 ('available' was requested)
mcd-DEBUG: 11/18/2010 08:11:28.804735: _mcd_dispatcher_add_connection: 0x879a4a0: 0x879cdc0 (/org/freedesktop/Telepathy/Connection/haze/icq/_3568211595)
mcd-DEBUG: 11/18/2010 08:11:28.804847: _mcd_connection_start_dispatching: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:11:28.805099: _mcd_connection_update_client_caps: ContactCapabilities unsupported
mcd-DEBUG: 11/18/2010 08:11:28.805160: mcd_connection_done_task_before_connect: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Calling Connect()
mcd-DEBUG: 11/18/2010 08:11:28.807056: on_connection_status_changed: status_changed called from tp (1)
mcd-DEBUG: 11/18/2010 08:11:28.807056: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:11:28.807058: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:28.807058: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:28.807058: mcd_account_changed_property: Forcibly emit PropertiesChanged now
mcd-DEBUG: 11/18/2010 08:11:28.807058: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:28.807095: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:28.807276: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:11:28.807286: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:11:28.807293: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:11:28.807308: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:11:28.807322: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:28.807327: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:28.875828: connect_cb: called for connection 0x879cdc0
mcd-DEBUG: 11/18/2010 08:11:31.479862: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:11:31.479954: mcd_connection_invalidated_cb: Proxy destroyed (Network error)!
mcd-DEBUG: 11/18/2010 08:11:31.479963: _mcd_connection_release_tp_connection: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:11:31.479974: _mcd_account_set_connection_status: haze/icq/_35682115950: 2 because 2
mcd-DEBUG: 11/18/2010 08:11:31.479974: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:31.479995: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 11/18/2010 08:11:31.480011: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 11/18/2010 08:11:31.480022: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:31.480030: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:31.480238: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:11:31.480247: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:11:31.480256: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:11:31.480279: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:11:31.480294: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:31.480300: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:31.480490: mcd_connection_invalidated_cb: Preparing for reconnection in 27 seconds
mcd-DEBUG: 11/18/2010 08:11:31.480505: on_connection_ready: got error: Network error
mcd-DEBUG: 11/18/2010 08:11:58.579674: mcd_connection_reconnect: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:11:58.579713: _mcd_connection_attempt: called for 0x879cdc0, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:58.579730: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:11:58.579806: _mcd_connection_connect: called for 0x879cdc0, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:58.579818: _mcd_connection_connect_with_params: Trying connect account: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:58.579839: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:11:58.579845: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:58.579853: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 11/18/2010 08:11:58.579858: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 11/18/2010 08:11:58.579868: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:58.579874: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:58.580269: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:11:58.580272: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:11:58.580296: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:11:58.580329: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:11:58.580346: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:58.580352: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:58.820955: request_connection_cb: created /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595
mcd-DEBUG: 11/18/2010 08:11:58.821365: _mcd_connection_set_tp_connection: new connection is 0x87c1d40
mcd-DEBUG: 11/18/2010 08:11:58.821377: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:58.821383: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:58.822182: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:11:58.824290: mcd_connection_early_get_statuses_cb: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Early Get(Statuses) succeeded
mcd-DEBUG: 11/18/2010 08:11:58.824301: presence_get_statuses_cb: account haze/icq/_35682115950:
mcd-DEBUG: 11/18/2010 08:11:58.824310: presence_get_statuses_cb:   busy
mcd-DEBUG: 11/18/2010 08:11:58.824315: presence_get_statuses_cb:   away
mcd-DEBUG: 11/18/2010 08:11:58.824320: presence_get_statuses_cb:   xa
mcd-DEBUG: 11/18/2010 08:11:58.824325: presence_get_statuses_cb:   available
mcd-DEBUG: 11/18/2010 08:11:58.824330: presence_get_statuses_cb:   hidden
mcd-DEBUG: 11/18/2010 08:11:58.824335: presence_get_statuses_cb:   offline
mcd-DEBUG: 11/18/2010 08:11:58.824345: _mcd_connection_set_presence: Setting status 'available' of type 2 ('available' was requested)
mcd-DEBUG: 11/18/2010 08:11:58.824606: _mcd_dispatcher_add_connection: 0x879a4a0: 0x879cdc0 (/org/freedesktop/Telepathy/Connection/haze/icq/_3568211595)
mcd-DEBUG: 11/18/2010 08:11:58.824719: _mcd_connection_start_dispatching: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:11:58.824968: _mcd_connection_update_client_caps: ContactCapabilities unsupported
mcd-DEBUG: 11/18/2010 08:11:58.825028: mcd_connection_done_task_before_connect: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Calling Connect()
mcd-DEBUG: 11/18/2010 08:11:58.828519: on_connection_status_changed: status_changed called from tp (1)
mcd-DEBUG: 11/18/2010 08:11:58.828536: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:11:58.828541: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:58.828550: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:11:58.828555: mcd_account_changed_property: Forcibly emit PropertiesChanged now
mcd-DEBUG: 11/18/2010 08:11:58.828560: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:58.828655: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:11:58.828814: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:11:58.828814: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:11:58.828814: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:11:58.828814: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:11:58.828814: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:11:58.828814: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:11:58.884252: connect_cb: called for connection 0x879cdc0
mcd-DEBUG: 11/18/2010 08:12:01.476775: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:12:01.476867: mcd_connection_invalidated_cb: Proxy destroyed (Network error)!
mcd-DEBUG: 11/18/2010 08:12:01.476876: _mcd_connection_release_tp_connection: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:12:01.476888: _mcd_account_set_connection_status: haze/icq/_35682115950: 2 because 2
mcd-DEBUG: 11/18/2010 08:12:01.476888: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:12:01.476888: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 11/18/2010 08:12:01.476888: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 11/18/2010 08:12:01.476888: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:12:01.476888: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:12:01.477150: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:12:01.477150: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:12:01.477150: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:12:01.477150: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:12:01.477158: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:12:01.477169: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:12:01.477360: mcd_connection_invalidated_cb: Preparing for reconnection in 81 seconds
mcd-DEBUG: 11/18/2010 08:12:01.477375: on_connection_ready: got error: Network error
mcd-DEBUG: 11/18/2010 08:13:22.652604: mcd_connection_reconnect: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:13:22.652637: _mcd_connection_attempt: called for 0x879cdc0, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:13:22.652719: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:13:22.652798: _mcd_connection_connect: called for 0x879cdc0, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:13:22.652811: _mcd_connection_connect_with_params: Trying connect account: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:13:22.652827: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:13:22.652833: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:13:22.652839: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 11/18/2010 08:13:22.652844: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 11/18/2010 08:13:22.652854: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:13:22.652861: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:13:22.653059: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:13:22.653069: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:13:22.653075: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:13:22.653105: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:13:22.653120: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:13:22.653126: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:13:22.875396: request_connection_cb: created /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595
mcd-DEBUG: 11/18/2010 08:13:22.875824: _mcd_connection_set_tp_connection: new connection is 0x87c1cc0
mcd-DEBUG: 11/18/2010 08:13:22.875838: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:13:22.875844: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:13:22.876666: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:13:22.878451: mcd_connection_early_get_statuses_cb: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Early Get(Statuses) succeeded
mcd-DEBUG: 11/18/2010 08:13:22.878459: presence_get_statuses_cb: account haze/icq/_35682115950:
mcd-DEBUG: 11/18/2010 08:13:22.878467: presence_get_statuses_cb:   busy
mcd-DEBUG: 11/18/2010 08:13:22.878473: presence_get_statuses_cb:   away
mcd-DEBUG: 11/18/2010 08:13:22.878478: presence_get_statuses_cb:   xa
mcd-DEBUG: 11/18/2010 08:13:22.878483: presence_get_statuses_cb:   available
mcd-DEBUG: 11/18/2010 08:13:22.878487: presence_get_statuses_cb:   hidden
mcd-DEBUG: 11/18/2010 08:13:22.878492: presence_get_statuses_cb:   offline
mcd-DEBUG: 11/18/2010 08:13:22.878499: _mcd_connection_set_presence: Setting status 'available' of type 2 ('available' was requested)
mcd-DEBUG: 11/18/2010 08:13:22.878751: _mcd_dispatcher_add_connection: 0x879a4a0: 0x879cdc0 (/org/freedesktop/Telepathy/Connection/haze/icq/_3568211595)
mcd-DEBUG: 11/18/2010 08:13:22.878860: _mcd_connection_start_dispatching: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:13:22.879111: _mcd_connection_update_client_caps: ContactCapabilities unsupported
mcd-DEBUG: 11/18/2010 08:13:22.879172: mcd_connection_done_task_before_connect: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Calling Connect()
mcd-DEBUG: 11/18/2010 08:13:22.880883: on_connection_status_changed: status_changed called from tp (1)
mcd-DEBUG: 11/18/2010 08:13:22.880898: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:13:22.880903: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:13:22.880912: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:13:22.880917: mcd_account_changed_property: Forcibly emit PropertiesChanged now
mcd-DEBUG: 11/18/2010 08:13:22.880920: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:13:22.881012: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:13:22.881109: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:13:22.881109: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:13:22.881109: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:13:22.881109: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:13:22.881109: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:13:22.881109: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:13:22.960339: connect_cb: called for connection 0x879cdc0
mcd-DEBUG: 11/18/2010 08:13:25.822001: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:13:25.822118: mcd_connection_invalidated_cb: Proxy destroyed (Network error)!
mcd-DEBUG: 11/18/2010 08:13:25.822127: _mcd_connection_release_tp_connection: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:13:25.822139: _mcd_account_set_connection_status: haze/icq/_35682115950: 2 because 2
mcd-DEBUG: 11/18/2010 08:13:25.822139: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:13:25.822139: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 11/18/2010 08:13:25.822139: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 11/18/2010 08:13:25.822139: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:13:25.822139: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:13:25.822393: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:13:25.822393: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:13:25.822393: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:13:25.822393: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:13:25.822400: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:13:25.822411: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:13:25.822602: mcd_connection_invalidated_cb: Preparing for reconnection in 243 seconds
mcd-DEBUG: 11/18/2010 08:13:25.822614: on_connection_ready: got error: Network error
mcd-DEBUG: 11/18/2010 08:17:28.677853: mcd_connection_reconnect: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:17:28.677887: _mcd_connection_attempt: called for 0x879cdc0, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:17:28.677906: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:17:28.677984: _mcd_connection_connect: called for 0x879cdc0, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:17:28.677997: _mcd_connection_connect_with_params: Trying connect account: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:17:28.678016: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:17:28.678021: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:17:28.678029: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 11/18/2010 08:17:28.678033: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 11/18/2010 08:17:28.678042: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:17:28.678047: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:17:28.678215: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:17:28.678231: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:17:28.678239: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:17:28.678267: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:17:28.678282: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:17:28.678288: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:17:28.894166: request_connection_cb: created /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595
mcd-DEBUG: 11/18/2010 08:17:28.894614: _mcd_connection_set_tp_connection: new connection is 0x87c1c40
mcd-DEBUG: 11/18/2010 08:17:28.894628: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:17:28.894634: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:17:28.895528: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:17:28.897238: mcd_connection_early_get_statuses_cb: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Early Get(Statuses) succeeded
mcd-DEBUG: 11/18/2010 08:17:28.897253: presence_get_statuses_cb: account haze/icq/_35682115950:
mcd-DEBUG: 11/18/2010 08:17:28.897260: presence_get_statuses_cb:   busy
mcd-DEBUG: 11/18/2010 08:17:28.897268: presence_get_statuses_cb:   away
mcd-DEBUG: 11/18/2010 08:17:28.897272: presence_get_statuses_cb:   xa
mcd-DEBUG: 11/18/2010 08:17:28.897277: presence_get_statuses_cb:   available
mcd-DEBUG: 11/18/2010 08:17:28.897281: presence_get_statuses_cb:   hidden
mcd-DEBUG: 11/18/2010 08:17:28.897286: presence_get_statuses_cb:   offline
mcd-DEBUG: 11/18/2010 08:17:28.897296: _mcd_connection_set_presence: Setting status 'available' of type 2 ('available' was requested)
mcd-DEBUG: 11/18/2010 08:17:28.897555: _mcd_dispatcher_add_connection: 0x879a4a0: 0x879cdc0 (/org/freedesktop/Telepathy/Connection/haze/icq/_3568211595)
mcd-DEBUG: 11/18/2010 08:17:28.897671: _mcd_connection_start_dispatching: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:17:28.897757: _mcd_connection_update_client_caps: ContactCapabilities unsupported
mcd-DEBUG: 11/18/2010 08:17:28.897821: mcd_connection_done_task_before_connect: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Calling Connect()
mcd-DEBUG: 11/18/2010 08:17:28.900183: on_connection_status_changed: status_changed called from tp (1)
mcd-DEBUG: 11/18/2010 08:17:28.900202: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:17:28.900207: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:17:28.900218: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:17:28.900223: mcd_account_changed_property: Forcibly emit PropertiesChanged now
mcd-DEBUG: 11/18/2010 08:17:28.900228: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:17:28.900321: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:17:28.900469: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:17:28.900469: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:17:28.900469: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:17:28.900469: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:17:28.900469: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:17:28.900469: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:17:28.954291: connect_cb: called for connection 0x879cdc0
mcd-DEBUG: 11/18/2010 08:17:32.485277: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:17:32.485304: mcd_connection_invalidated_cb: Proxy destroyed (Network error)!
mcd-DEBUG: 11/18/2010 08:17:32.485317: _mcd_connection_release_tp_connection: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:17:32.485332: _mcd_account_set_connection_status: haze/icq/_35682115950: 2 because 2
mcd-DEBUG: 11/18/2010 08:17:32.485344: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:17:32.485352: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 11/18/2010 08:17:32.485358: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 11/18/2010 08:17:32.485368: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:17:32.485374: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:17:32.485584: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:17:32.485594: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:17:32.485603: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:17:32.485627: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:17:32.485644: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:17:32.485649: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:17:32.485842: mcd_connection_invalidated_cb: Preparing for reconnection in 729 seconds
mcd-DEBUG: 11/18/2010 08:17:32.485857: on_connection_ready: got error: Network error
mcd-DEBUG: 11/18/2010 08:18:54.49529: get_mcddbusprop: org.freedesktop.Telepathy.Account, RequestedPresence
mcd-DEBUG: 11/18/2010 08:18:54.49551: set_requested_presence: called for haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:18:54.49562: set_requested_presence: setting requested presence: 1, offline, 
mcd-DEBUG: 11/18/2010 08:18:54.49573: mcd_account_request_presence_int: Combined presence: 1 offline 
mcd-DEBUG: 11/18/2010 08:18:54.49582: mcd_account_changed_property: called: ChangingPresence
mcd-DEBUG: 11/18/2010 08:18:54.49588: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:18:54.49604: _mcd_connection_request_presence: Presence requested: 1
mcd-DEBUG: 11/18/2010 08:18:54.49623: mcd_account_changed_property: called: RequestedPresence
mcd-DEBUG: 11/18/2010 08:18:54.67962: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:18:54.123717: _mcd_connection_update_client_caps: ContactCapabilities unsupported
mcd-DEBUG: 11/18/2010 08:19:17.975486: dbusprop_get_all: org.freedesktop.Telepathy.AccountManager
mcd-DEBUG: 11/18/2010 08:19:17.975516: get_valid_accounts: called
mcd-DEBUG: 11/18/2010 08:19:17.975528: get_invalid_accounts: called
mcd-DEBUG: 11/18/2010 08:19:17.975537: mcd_dbus_get_interfaces: called
mcd-DEBUG: 11/18/2010 08:19:18.200313: _mcd_client_registry_found_name: Registering client org.freedesktop.Telepathy.Client.Empathy.EventManager
mcd-DEBUG: 11/18/2010 08:19:18.200313: mcd_client_proxy_constructed: org.freedesktop.Telepathy.Client.Empathy.EventManager
mcd-DEBUG: 11/18/2010 08:19:18.200313: mcd_client_proxy_introspect: No .client file for org.freedesktop.Telepathy.Client.Empathy.EventManager. Ask on D-Bus.
mcd-DEBUG: 11/18/2010 08:19:18.442013: _mcd_client_registry_found_name: Registering client org.freedesktop.Telepathy.Client.Empathy.FileTransfer
mcd-DEBUG: 11/18/2010 08:19:18.442030: mcd_client_proxy_constructed: org.freedesktop.Telepathy.Client.Empathy.FileTransfer
mcd-DEBUG: 11/18/2010 08:19:18.442238: mcd_client_proxy_introspect: No .client file for org.freedesktop.Telepathy.Client.Empathy.FileTransfer. Ask on D-Bus.
mcd-DEBUG: 11/18/2010 08:19:18.472719: dbusprop_get_all: org.freedesktop.Telepathy.Account
mcd-DEBUG: 11/18/2010 08:19:18.472744: mcd_dbus_get_interfaces: called
mcd-DEBUG: 11/18/2010 08:19:18.472819: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:19:18.472851: get_connect_automatically: called for haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:19:18.473526: dbusprop_get_all: org.freedesktop.Telepathy.Account
mcd-DEBUG: 11/18/2010 08:19:18.473526: mcd_dbus_get_interfaces: called
mcd-DEBUG: 11/18/2010 08:19:18.473541: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:19:18.473634: get_connect_automatically: called for haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:19:18.474973: _mcd_client_proxy_add_interfaces: org.freedesktop.Telepathy.Client.Empathy.EventManager: org.freedesktop.Telepathy.Client.Approver
mcd-DEBUG: 11/18/2010 08:19:18.474988: _mcd_client_proxy_get_interfaces_cb: Client org.freedesktop.Telepathy.Client.Empathy.EventManager
mcd-DEBUG: 11/18/2010 08:19:18.474996: _mcd_client_proxy_get_interfaces_cb: org.freedesktop.Telepathy.Client.Empathy.EventManager is an Approver
mcd-DEBUG: 11/18/2010 08:19:18.499541: _mcd_client_proxy_add_interfaces: org.freedesktop.Telepathy.Client.Empathy.FileTransfer: org.freedesktop.Telepathy.Client.Handler
mcd-DEBUG: 11/18/2010 08:19:18.499556: _mcd_client_proxy_get_interfaces_cb: Client org.freedesktop.Telepathy.Client.Empathy.FileTransfer
mcd-DEBUG: 11/18/2010 08:19:18.499561: _mcd_client_proxy_get_interfaces_cb: org.freedesktop.Telepathy.Client.Empathy.FileTransfer is a Handler
mcd-DEBUG: 11/18/2010 08:19:18.501616: mcd_client_registry_ready_cb: org.freedesktop.Telepathy.Client.Empathy.EventManager
mcd-DEBUG: 11/18/2010 08:19:18.503016: get_mcddbusprop: org.freedesktop.Telepathy.Account, RequestedPresence
mcd-DEBUG: 11/18/2010 08:19:18.503031: set_requested_presence: called for haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:19:18.503040: set_requested_presence: setting requested presence: 2, available, 
mcd-DEBUG: 11/18/2010 08:19:18.503050: mcd_account_request_presence_int: Combined presence: 2 available 
mcd-DEBUG: 11/18/2010 08:19:18.503056: mcd_account_changed_property: called: ChangingPresence
mcd-DEBUG: 11/18/2010 08:19:18.503061: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:19:18.503073: _mcd_connection_request_presence: Presence requested: 2
mcd-DEBUG: 11/18/2010 08:19:18.503079: _mcd_connection_set_presence: tp_conn is NULL
mcd-DEBUG: 11/18/2010 08:19:18.503086: _mcd_connection_attempt: called for 0x879cdc0, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:19:18.503093: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:19:18.503185: _mcd_connection_connect: called for 0x879cdc0, account haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:19:18.503191: _mcd_connection_connect_with_params: Trying connect account: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:19:18.503204: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:19:18.503204: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:19:18.503204: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 11/18/2010 08:19:18.503204: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 11/18/2010 08:19:18.503204: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:19:18.503204: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:19:18.503205: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:19:18.503217: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:19:18.503236: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:19:18.503251: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:19:18.503256: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:19:18.503586: mcd_account_changed_property: called: RequestedPresence
mcd-DEBUG: 11/18/2010 08:19:18.503592: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:19:18.512816: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:19:18.568403: _mcd_client_proxy_handler_get_all_cb: org.freedesktop.Telepathy.Client.Empathy.FileTransfer has 1 HandlerChannelFilter entries
mcd-DEBUG: 11/18/2010 08:19:18.568454: _mcd_client_proxy_handler_get_all_cb: org.freedesktop.Telepathy.Client.Empathy.FileTransfer has BypassApproval=F
mcd-DEBUG: 11/18/2010 08:19:18.568506: _mcd_connection_update_client_caps: ContactCapabilities unsupported
mcd-DEBUG: 11/18/2010 08:19:18.568533: mcd_client_registry_ready_cb: org.freedesktop.Telepathy.Client.Empathy.FileTransfer
mcd-DEBUG: 11/18/2010 08:19:18.784854: request_connection_cb: created /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595
mcd-DEBUG: 11/18/2010 08:19:18.785345: _mcd_connection_set_tp_connection: new connection is 0x87c1bc0
mcd-DEBUG: 11/18/2010 08:19:18.785358: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:19:18.785365: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:19:18.786113: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:19:18.788358: mcd_connection_early_get_statuses_cb: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Early Get(Statuses) succeeded
mcd-DEBUG: 11/18/2010 08:19:18.788379: presence_get_statuses_cb: account haze/icq/_35682115950:
mcd-DEBUG: 11/18/2010 08:19:18.788388: presence_get_statuses_cb:   busy
mcd-DEBUG: 11/18/2010 08:19:18.788393: presence_get_statuses_cb:   away
mcd-DEBUG: 11/18/2010 08:19:18.788398: presence_get_statuses_cb:   xa
mcd-DEBUG: 11/18/2010 08:19:18.788403: presence_get_statuses_cb:   available
mcd-DEBUG: 11/18/2010 08:19:18.788408: presence_get_statuses_cb:   hidden
mcd-DEBUG: 11/18/2010 08:19:18.788413: presence_get_statuses_cb:   offline
mcd-DEBUG: 11/18/2010 08:19:18.788422: _mcd_connection_set_presence: Setting status 'available' of type 2 ('available' was requested)
mcd-DEBUG: 11/18/2010 08:19:18.788680: _mcd_dispatcher_add_connection: 0x879a4a0: 0x879cdc0 (/org/freedesktop/Telepathy/Connection/haze/icq/_3568211595)
mcd-DEBUG: 11/18/2010 08:19:18.788798: _mcd_connection_start_dispatching: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:19:18.789045: _mcd_connection_update_client_caps: ContactCapabilities unsupported
mcd-DEBUG: 11/18/2010 08:19:18.789107: mcd_connection_done_task_before_connect: /org/freedesktop/Telepathy/Connection/haze/icq/_3568211595: Calling Connect()
mcd-DEBUG: 11/18/2010 08:19:18.791492: on_connection_status_changed: status_changed called from tp (1)
mcd-DEBUG: 11/18/2010 08:19:18.791511: _mcd_account_set_connection_status: haze/icq/_35682115950: 1 because 1
mcd-DEBUG: 11/18/2010 08:19:18.791517: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:19:18.791524: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:19:18.791529: mcd_account_changed_property: Forcibly emit PropertiesChanged now
mcd-DEBUG: 11/18/2010 08:19:18.791534: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:19:18.791630: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:19:18.791763: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:19:18.791763: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:19:18.791763: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:19:18.791763: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:19:18.791763: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:19:18.791763: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:19:18.856544: connect_cb: called for connection 0x879cdc0
mcd-DEBUG: 11/18/2010 08:19:21.858990: on_connection_status_changed: status_changed called from tp (2)
mcd-DEBUG: 11/18/2010 08:19:21.859082: mcd_connection_invalidated_cb: Proxy destroyed (Network error)!
mcd-DEBUG: 11/18/2010 08:19:21.859091: _mcd_connection_release_tp_connection: 0x879cdc0
mcd-DEBUG: 11/18/2010 08:19:21.859102: _mcd_account_set_connection_status: haze/icq/_35682115950: 2 because 2
mcd-DEBUG: 11/18/2010 08:19:21.859102: mcd_account_freeze_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:19:21.859102: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 11/18/2010 08:19:21.859102: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 11/18/2010 08:19:21.859102: mcd_account_changed_property: called: Connection
mcd-DEBUG: 11/18/2010 08:19:21.859102: mcd_account_changed_property: First changed property
mcd-DEBUG: 11/18/2010 08:19:21.859323: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 11/18/2010 08:19:21.859333: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 11/18/2010 08:19:21.859342: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 11/18/2010 08:19:21.859368: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 11/18/2010 08:19:21.859384: mcd_account_thaw_properties: haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:19:21.859389: emit_property_changed: called
mcd-DEBUG: 11/18/2010 08:19:21.859577: mcd_connection_invalidated_cb: Preparing for reconnection in 1800 seconds
mcd-DEBUG: 11/18/2010 08:19:21.859592: on_connection_ready: got error: Network error
mcd-DEBUG: 11/18/2010 08:20:57.635888: dbusprop_get_all: org.freedesktop.Telepathy.AccountManager
mcd-DEBUG: 11/18/2010 08:20:57.635900: get_valid_accounts: called
mcd-DEBUG: 11/18/2010 08:20:57.635925: get_invalid_accounts: called
mcd-DEBUG: 11/18/2010 08:20:57.635945: mcd_dbus_get_interfaces: called
mcd-DEBUG: 11/18/2010 08:20:57.637650: dbusprop_get_all: org.freedesktop.Telepathy.Account
mcd-DEBUG: 11/18/2010 08:20:57.637665: mcd_dbus_get_interfaces: called
mcd-DEBUG: 11/18/2010 08:20:57.637726: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:20:57.637799: get_connect_automatically: called for haze/icq/_35682115950
mcd-DEBUG: 11/18/2010 08:20:57.638458: dbusprop_get_all: org.freedesktop.Telepathy.Account
mcd-DEBUG: 11/18/2010 08:20:57.638458: mcd_dbus_get_interfaces: called
mcd-DEBUG: 11/18/2010 08:20:57.638474: _mcd_account_dup_parameters: called
mcd-DEBUG: 11/18/2010 08:20:57.638578: get_connect_automatically: called for haze/icq/_35682115950

```

---

### Post by LTS_G on 2010-11-18
On the link below is a fix for Empathy:

[https://bugs.launchpad.net/empathy/+bug/676060](https://bugs.launchpad.net/empathy/+bug/676060)

Put this in your console:
mc-tool list
show you the list of accounts. All you need is haze/icq/_(account Number)
 mc-tool update haze/icq/_(account Number)  bool:use-ssl=0


This is not a good fix, because without SSL the connection is not save. But till the fix it will work.

---

### Post by scr3amingeagle on 2010-11-18
still can't get it working for empathy but updated pidgin to 2.7.3 and it is working, guess i had an old version.

---

### Post by VinDSL on 2010-11-18
I've never *liked* Empathy.  I'm a Pidgin fanboi...

I don't know when Ubu changed the default IM client to Empathy, but I've always deleted Empathy and installed Pidgin, until 10.10.

I decided to test my petty bias, and give Empathy another try, but this tears it!

I just installed Pidgin in 10.10 and had ICQ (sans SSL) in 2 minutes.

Truthfully, I'll *never* run Empathy again...  :P

---

### Post by apoapo on 2010-11-18
May i ask you a question?

Do you run pidgin with th emessagign menu of Gnome? My podgin crashes everytime i open new messages through this green envelope.

Im kind of forced to use empathy.. :(

---

### Post by VinDSL on 2010-11-18
> **apoapo said:**
> Do you run pidgin with th emessagign menu of Gnome? My podgin crashes everytime i open new messages through this green envelope.[...]I don't understand the question, but...

Here's what I'm running.  Pidgin is working fine...  ;)


(Click image for full-size view)
[INDENT][[IMG]http://vindsl.com/images/pidgin-18-nov-2010(550x440).png[/IMG]]("http://vindsl.com/images/pidgin-18-nov-2010.png")
[/INDENT]

---

### Post by apoapo on 2010-11-18
That's what i talked about. I really wonder why i can  reproduce iton every ubuntu i can get my hands on but nobody else experiences it xD anyway..it's OT. Thx for your reply

---

### Post by Stoneface on 2010-11-19
> **LTS_G said:**
> On the link below is a fix for Empathy:

[https://bugs.launchpad.net/empathy/+bug/676060](https://bugs.launchpad.net/empathy/+bug/676060)

Put this in your console:
mc-tool list
show you the list of accounts. All you need is haze/icq/_(account Number)
 mc-tool update haze/icq/_(account Number)  bool:use-ssl=0


This is not a good fix, because without SSL the connection is not save. But till the fix it will work.

Thanks LTS_G. Worked. Even though is not *the* solution, it is the only one I got for now..

P.S. Replied a bit slow as I could not log on to the Ubuntu Forums several times last night. Kept on being sent to the login form :-(

---

### Post by Orange Kingdom on 2010-11-19
Today it doesn't work anymore :confused:

Why is it so unstable?

Looks like a game: how to disable as many ubuntu messenger apps as possible.

Which server to use this time?
I am using login.icq.com

---

### Post by apoapo on 2010-11-19
Works fine here.

---

### Post by Orange Kingdom on 2010-11-19
Which login server?

---

### Post by Orange Kingdom on 2010-11-19
With this:  [https://bugs.launchpad.net/empathy/+bug/676060](https://bugs.launchpad.net/empathy/+bug/676060)

It works again with empathy.

---

### Post by -bug- on 2010-11-30
Using Empathy 2.30.3 on Lucid, I also had this problem 2 weeks ago, and could solve it by setting the server to 'login.icq.com' and setting use-ssl false. But since today I'm having troubles again, getting 'Network error' when I try to connect. I think, there might have been an libpurple update in between, but I am not certain. (How can I see what has been updated last?)
Anyone else experiencing the same? Which settings should be used to make it work again?

---

### Post by Carlin0 on 2010-11-30
with empathy don't work ...

---

### Post by yarozar on 2010-11-30
Two weeks ago when ICQ stopped working I have just disabled it in Empathy. Today I acidently turned it on and, surprise-surprise - it worked. :)

I did not do *any* manual intrusions.

---

### Post by apoapo on 2010-11-30
I had to switch use ssl back on!

```
mc-tool update haze/icq/_3<yournumber>0 bool:use-ssl=1
```

---

### Post by Iscander on 2010-12-01
> **apoapo said:**
> I had to switch use ssl back on!

```
mc-tool update haze/icq/_3<yournumber>0 bool:use-ssl=1
```

This don't work for me :-(

---

### Post by apoapo on 2010-12-01
You are on Ubuntu Maverick using Empathy? All updates done?

This is the serv i'm using: login.icq.com
The iso code: ISO 8859-1
And SSL is on. 


I have no problems. Exception: from time to time i have to hit reconnect.

---

### Post by -bug- on 2010-12-01
I had the same idea, but it doesn't work, no matter if ssl is switched on or off.
The port is set to 5190 and server is login.icq.com - any suggestions which settings should work?

I set ISO-8859-15 (I think I changed that once because of some strange German letters, but changing that doesn't help to connect)
I'm on Lucid with all available updates. Maybe it has been fixed for Maverick already and the LTS policy says, one has to wait a week until changes are done to make sure they are stable?

---

### Post by lolbot on 2010-12-01
Hi,

i got it working. I`ve unchecked first and second option and checked third (AIM/ICQ proxy server) in ICQ account settings.

cheers

---

### Post by -bug- on 2010-12-02
Which options are you talking about? Where to find them?
Better questions might be: Which version are you using? And are you on Lucid or Maverick?

---

### Post by m-f-a on 2010-12-04
Hey guys,

I had the same problem with empathy, but I got it working now. The problem seems to be the client-login option.

You can fix this by running the following command in a terminal:
```
mc-tool update haze/icq/_3<your icq number>0 bool:use-clientlogin=0
```

-- edit --
I have turned off ssl, by the way.

Cheers,
m-f-a

---

### Post by -bug- on 2010-12-05
Thanks, that made the change for me!
The use-clientlogin option did not show up (with mc-tool show) until I set it, as you described. ICQ working again for me, if I want to use it without SSL...

---

### Post by Iscander on 2010-12-06
> **m-f-a said:**
> Hey guys,

I had the same problem with empathy, but I got it working now. The problem seems to be the client-login option.

You can fix this by running the following command in a terminal:
```
mc-tool update haze/icq/_3<your icq number>0 bool:use-clientlogin=0
```

-- edit --
I have turned off ssl, by the way.

Cheers,
m-f-a

On Lucid this works fine, thx ;)
On Maverick enough to disable ssl.

---

### Post by charliestoned on 2010-12-19
> **m-f-a said:**
> 

... 

You can fix this by running the following command in a terminal:
```
mc-tool update haze/icq/_3<your icq number>0 bool:use-clientlogin=0
```

-- edit --
I have turned off ssl, by the way.

... 

m-f-a

THX, this worked fine!! 

Cheers, 
Stefan

---

### Post by vivedekananda on 2010-12-27
my ICQ uin was stolen shortly after I disabled ssl;
good bye icq, I was getting tired of regular login problems anyway

---

