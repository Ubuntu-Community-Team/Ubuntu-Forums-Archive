---
title: "ssh and nvc not working"
date: 2008-01-01
forum: Mythbuntu
---

### Post by lime4x4 on 2008-01-01
i have it enabled in the control center but can't access the mythtv box from another linux machine. I keep getting the following error
Connection failed. No server running at the given address and port.

---

### Post by elj4176 on 2008-01-03
A couple things to check -

Look to see if ssh is actually running on the mythbox

If ssh is running then try:

ssh yourusernameonthemythbox@themythboxipaddress -p 22

an example: ssh elj4176@192.168.1.255 -p 22


As for vnc - I don't use it so I can't  help you there.
Hope that helps.

---

### Post by Mithrilhall on 2008-01-03
```

ps -e | grep vnc

```

Do you see it running anywhere?

---

