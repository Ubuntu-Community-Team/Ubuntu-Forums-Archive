---
title: "suspend and resume with remote"
date: 2008-11-21
forum: Mythbuntu
---

### Post by Andycas on 2008-11-21
I've read a lot of posts about lirc and suspending to ram, however i havent figured out how to accomplish that. Ive tried using irexec to suspend with these lines in .lircrc:
```
begin
    prog = irexec
    button = yellow
    config = /etc/acpi/sleep.sh
end

begin
    prog = irexec
    button = blue
    config = /etc/acpi/resume.sh
end
```
But when i try "/etc/acpi/sleep.sh" in terminal i get no output, ofcourse irexec doesnt do anything either.
I havent found any good HOWTO's for it (there are some, but it doesnt involve waking up with remote), maybe someone could explain this?:(

---

### Post by Milan Knizek on 2008-11-25
Ubuntu uses pmi scripts rather then other methods. You should first try to run "sudo pm-suspend" to see if it works as expected.

You might also have problems with waking up using a remote - depending on the motherboard. I use lenovo z60m and it switches off IrDA on suspend, so I cannot power it back with a remote.

---

