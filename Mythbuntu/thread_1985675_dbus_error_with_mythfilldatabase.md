---
title: "dbus error with mythfilldatabase"
date: 2012-05-23
forum: Mythbuntu
---

### Post by rdege on 2012-05-23
Back on My 7th, I upgrade mythbuntu from 11.10 to 12.04.  Since then, I have been receiving these errors in the auth.log file:


May 23 07:38:16 dbus[820]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.26" (uid=109 pid=21235 comm="/usr/bin/mythfilldatabase --verbose general --logl") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=1021 comm="NetworkManager ")

May 23 07:38:17 dbus[820]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.26" (uid=109 pid=21235 comm="/usr/bin/mythfilldatabase --verbose general --logl") interface="org.freedesktop.NetworkManager" member="GetDevices" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=1021 comm="NetworkManager ")


Does anyone know what these errors mean, and if it's something I should be concerned about?

-Rob

---

