---
title: "way too much traffic on dbus from wicd"
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by kgoess on 2012-01-24
Dbus is driving my cpu load up to 50% every couple of seconds.  Strace output is about 200k/sec of data.  It's these two messages over and over.  Any suggestions on how I can shut this up?

recvmsg(36, {msg_name(0)=NULL, msg_iov(1)=[{"l\1\0\1\0\0\0\0-Ps\0[\0\0\0\1\1o\0\20\0\0\0/org/wicd/daemon\0\0\0\0\0\0\0\0\6\1s\0\5\0\0\0:1.12\0\0\0\2\1s\0\17\0\0\0org.wicd.daemon\0\3\1s\0\n\0\0\0GetSuspend\0\0\0\0\0\0tus\0\0\0\0\0\10\1g\0\2vv\0\1i\0\0\3\0\0\0\2as\0\21\0\0\0\f\0\0\000192.168.1.28\0\00028\0\0001\0\0ce='org.wicd.daemon',member='SignalBackendChanged'\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 2048}],

sendmsg(17, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\0\1\0\0\0\0.Ps\0v\0\0\0\1\1o\0\20\0\0\0/org/wicd/daemon\0\0\0\0\0\0\0\0\6\1s\0\5\0\0\0:1.12\0\0\0\2\1s\0\17\0\0\0org.wicd.daemon\0\3\1s\0\21\0\0\0CheckIfConnecting\0\0\0\0\0\0\0\7\1s\0\5\0\0\0:1.31\0\0\0", 136}, {"", 0}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 136
recvmsg(17, {msg_name(0)=NULL, msg_iov(1)=[{"l\2\1\1\4\0\0\0G8\230\0\37\0\0\0\6\1s\0\5\0\0\0:1.31\0\0\0\5\1u\0.Ps\0\10\1g\0\1b\0\0\0\0\0\0\0\0\0\0\00068.1.28\0\0aemon\0\3\1s\0\v\0\0\0UpdateState\0\0\0\0\0l\2\1\1\0\0\0\0@8\230\0\30\0\0\0\6\1s\0\5\0\0\0:1.48\0\0\0\5\1u\0-\254\22\0\0pdateState\0\0\0\0\0l\2\1\1\0\0\0\0@8\230\0\30\0\0\0\6\1s\0\5\0\0\0:1.48\0\0\0\5\1u\0-\254\22\0\0\5\1u\0\310\253\22\0\0\21\0\0emon\0\0\0\0\0\0\0\0\2\1s\0\17\0\0\0org.wicd.daemon\0\3\1s\0\v\0\0\0UpdateState\0\0\0\0\0l\2\1\1\0\0\0\0\26\3508\0\30\0\0\0\6\1s\0\5\0\0\0:1.48\0\0\0\5\1u\0\235\270\6\0\0\"Introspect\">\n      <arg direction=\"out\" type=\"s\" />\n    </method>\n  </interface>\n  <interface name=\"org.wicd.daemon.wired\">\n    <method name=\"CheckWiredConnectingMessage\">\n    </method>\n    <method name=\"D"..., 2048}],

---

### Post by kgoess on 2012-02-04
I went back from wicd to network-manager, since I gave up on trying to get wifi to work I don't need wicd any more.

---

