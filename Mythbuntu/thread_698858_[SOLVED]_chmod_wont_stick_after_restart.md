---
title: "[SOLVED] chmod wont stick after restart"
date: 2008-02-16
forum: Mythbuntu
---

### Post by volkswagner on 2008-02-16
I am trying to modify the permisions to the following file.

/dev/input/by-id//usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd


I have tried the following but it only allows access until a restart then setting go back to root access only and others none permission.

```
sudo chmod -R 755 /dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd

```

and

```
sudo chmod -R 777 /dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd

```

and

```
sudo chown -R eric:eric /dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd

```

and

```
sudo chmod -R 777 /dev/input/by-id
```

why wont the change stick after a restart?

---

### Post by superm1 on 2008-02-16
Those devices are created dynamically on boot.  You will need to create a udev rule that sets the permissions.

---

### Post by volkswagner on 2008-02-17
Thanks for the reply.

I created the udev rule with the help of this thread.

[http://ubuntuforums.org/showthread.php?t=168221]("http://ubuntuforums.org/showthread.php?t=168221")

I added user, group, and mode arguments.

---

