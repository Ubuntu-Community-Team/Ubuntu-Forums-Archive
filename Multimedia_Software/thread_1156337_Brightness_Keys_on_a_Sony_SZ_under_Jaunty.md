---
title: "Brightness Keys on a Sony SZ under Jaunty"
date: 2009-05-11
forum: Multimedia Software
---

### Post by carljmoss on 2009-05-11
It's been documented elsewhere (see _[here]("http://ubuntuforums.org/showthread.php?t=1004568")_) how to get the brightness keys working on a Sony FZ series under Jaunty. For the sake of completeness, here's how to do it on a Sony SZ:

1. Make sure **nvclock** is installed

```
sudo apt-get install nvclock
```

2. In /etc/acpi/events create a file **sony-brightness-up** containing the following:

```
# /etc/acpi/events/sony-brightness-up
event=sony/hotkey SPIC 00000001 00000011
action=/etc/acpi/sonybright.sh up
```

3. In /etc/acpi/events create a file **sony-brightness-down** containing the following:

```
# /etc/acpi/events/sony-brightness-down
event=sony/hotkey SPIC 00000001 00000010
action=/etc/acpi/sonybright.sh down
```

4. In /etc/acpi create a file **sonybright.sh** containing the following:

```
#!/bin/bash
if [ "x$1" = "xdown" ]; then
# Decrease brightness
        nvclock -S -10
elif [ "x$1" = "xup" ]; then
# Increase brightness
        nvclock -S +10
elif [ "x$1" = "xdim" ]; then
# Minimum brightness
        nvclock -S 15
elif [ "x$1" = "xbright" ]; then
# Maximum brightness
        nvclock -S 100
else
   echo >&2 Unknown argument $1 to nvclock in sonybright.sh
fi
```

and make it executable

```
sudo chmod +x sonybright.sh
```

5. Restart **acpid**

```
sudo /etc/init.d/acpid restart
```

---

