---
title: "banshee media player wont start"
date: 2010-11-12
forum: Multimedia Software
---

### Post by ddr3XD on 2010-11-12
Banshee Media Player wont start. The loading icon appears and a tab that says "Starting Banshee Media Player" but it just dissappers and nothing happens.

Can anyone help me?

I'm using Ubuntu 10.10 Maverick

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
Which version of banshee are you using? Also did you try to launch it from the terminal to see the output?

---

### Post by ddr3XD on 2010-11-12
Banshee 1.8. And i dont know how to run from terminal :(

Thanks for quick reply

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
OK! Launch a terminal, type banshee or banshee-1 and hit enter. Then post the output here.

---

### Post by ddr3XD on 2010-11-12
This is what i get:

jayjay@jayjay-desktop:~$ banshee

** (/usr/lib/banshee-1/Banshee.exe:7909): WARNING **: The following assembly referenced from /usr/lib/banshee-1/Banshee.Services.dll could not be loaded:
     Assembly:   glib-sharp    (assemblyref_index=11)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee-1/).


** (/usr/lib/banshee-1/Banshee.exe:7909): WARNING **: Could not load file or assembly 'glib-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

** (/usr/lib/banshee-1/Banshee.exe:7909): WARNING **: The following assembly referenced from /usr/lib/banshee-1/Banshee.Services.dll could not be loaded:
     Assembly:   NDesk.DBus    (assemblyref_index=14)
     Version:    1.0.0.0
     Public Key: f6716e4f9b2ed099
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee-1/).


** (/usr/lib/banshee-1/Banshee.exe:7909): WARNING **: Could not load file or assembly 'NDesk.DBus, Version=1.0.0.0, Culture=neutral, PublicKeyToken=f6716e4f9b2ed099' or one of its dependencies.
Stacktrace:


Native stacktrace:

    banshee-1() [0x80c9774]
    banshee-1() [0x80f5753]
    [0xb783d40c]
    banshee-1() [0x80893db]
    banshee-1() [0x8061698]
    banshee-1() [0x8062e78]
    banshee-1() [0x806374f]
    banshee-1(mono_runtime_exec_main+0xde) [0x8103e9e]
    banshee-1(mono_runtime_run_main+0x15a) [0x810461a]
    banshee-1(mono_main+0x18c4) [0x80b2744]
    banshee-1() [0x805ad75]
    /lib/libc.so.6(__libc_start_main+0xe7) [0xb75b9ce7]
    banshee-1() [0x805acb1]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
jayjay@jayjay-desktop:~$

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
Try this command in terminal:
```

sudo apt-get install libglib2.0-cli

```

If that doesn't work try:

```

sudo apt-get install libglib2.0-cli-dev

```

tell me how it goes

---

### Post by ddr3XD on 2010-11-12
[FONT=monospace]For both commands it says:

[/FONT]```
jayjay@jayjay-desktop:~$ sudo apt-get install libglib2.0-cli
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libglib2.0-cli
E: Couldn't find any package by regex 'libglib2.0-cli'
[FONT=monospace]jayjay@jayjay-desktop:~$[/FONT]

```[FONT=monospace]

does the same for the other command
[/FONT]

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
Oh, sorry, my bad! It's cil not cli! Use the same command with cil instead of cli. Cli stands for Command Line Interface, aka terminal so it's a mistake anyone can make:)


PS: actually the right way to say it is that  when you work with the terminal you use a CLI. And when you work with the mouse you're using a GUI - graphical user interface. I'm saying this to avoid getting lynched.

---

### Post by ddr3XD on 2010-11-12
Still wont start. Thanks for the help tho.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
Did it install libglib2.0-cil or was it already installed? Also is the output on terminal still the same when you run banshee?

---

### Post by ddr3XD on 2010-11-12
libglib2.0-cil was already installed. when i ran it i got: 
> libglib2.0-cil is already the newest versionI still get same exact output command as first when banshee is ran from terminal

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
Also try this command:

```
sudo apt-get install libgkeyfile1.0-cil
```

---

### Post by ddr3XD on 2010-11-12
> **&#24746 said:**
> Also try this command:

```
sudo apt-get install libgkeyfile1.0-cil
```

i get:
> libgkeyfile1.0-cil is already the newest version.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
w8. I'm trying to find some help on the irc network...

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
OK! I got no love on the irc channel! Try this even though i'm not sure it will help:

```
sudo gacutil -i /usr/lib/cli/glib-sharp-2.0/glib-sharp.dll
```

---

### Post by Quadunit404 on 2010-11-12
If the above doesn't work... Try deleting ~/.config/banshee-1/addin-db-001. Usually if Banshee doesn't work for me for whatever reason deleting that works wonders (it'll be recreated when you start Banshee again) but you'll need to reset your enabled extensions after :|

---

### Post by ddr3XD on 2010-11-12
> **&#24746 said:**
> OK! I got no love on the irc channel! Try this even though i'm not sure it will help:

```
sudo gacutil -i /usr/lib/cli/glib-sharp-2.0/glib-sharp.dll
```

Still nothing :(

> **Quadunit404 said:**
> If the above doesn't work... Try deleting  ~/.config/banshee-1/addin-db-001. Usually if Banshee doesn't work for me  for whatever reason deleting that works wonders (it'll be recreated  when you start Banshee again) but you'll need to reset your enabled  extensions after :neutral:

The only file in my ~/.config/banshee-1 folder is a log file.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
What about this:

```
sudo gacutil -i /usr/lib/cli/Mono.Addins-0.2/Mono.Addins.dll
```

these commands are supposed to install the assemblies needed but if they don't work it will be hard for me to find the solution.

---

### Post by ddr3XD on 2010-11-12
it installed:
> Installed /usr/lib/cli/Mono.Addins-0.2/Mono.Addins.dll into the gac (/usr/local/lib/mono/gac)
but still wont start

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
To be honest I haven't really used mono so i'm not very familiar with it. Of course I've used apps written in mono such as Banshee and F-spot but I've never had a problem like that. When did this problem start? Where you able to use banshee before?

---

### Post by ddr3XD on 2010-11-12
No biggie. I actually wanted to try Banshee because of a feature it had that i thought Rhythmbox didnt have, but then while trying to solve this problem i found out that Rhythmbox did have this feature after-all. But i still wanted to get it fix in-case i decide to switch to Banshee later. This is my first time installing and trying to run Banshee. I installed it today but it wont run. kind of disappointing being as i heard it was suppose to be the new default player for Ubuntu 11.04 Natty Narwhal. Hopefully if and when i upgrade to Natty it runs well. If not i will rage XD.

Thanks for your help tho. i appreciate it. :)

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
I wasn't really much of a help. Rhythmbox is fine but I'm using Banshee too. At least until Nightingale comes out. I noticed that banshee couldn't find ndesk.dbus too. Could you try typing this in terminal?

```

sudo apt-get install libndesk-dbus-glib1.0-cil && libndesk-dbus1.0-cil

```

If they're already installed i'll tell you how to install the assembler but i'm looking for the right path at the moment

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
Thanks for your request! Did I add you? I can' tell:)

PS: I'm a total noob when it comes to this forum. I can't seem to find how to do stuff(no offence to the admins)

---

### Post by ddr3XD on 2010-11-12
libndesk-dbus-glib1.0-cil was already installed.
BUT for libndesk:
> libndesk-dbus1.0-cil: command not foundill paste everything just for clarity:

> jayjay@jayjay-desktop:~$ sudo apt-get install libndesk-dbus-glib1.0-cil && libndesk-dbus1.0-cil
[sudo] password for jayjay: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libndesk-dbus-glib1.0-cil is already the newest version.
The following package was automatically installed and is no longer required:
  hplip-cups
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
libndesk-dbus1.0-cil: command not found
jayjay@jayjay-desktop:~$

I really do admire your perseverance ;)
Yes you did add me. LOL

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
Haha! Thank you! Again I was reckless. I should have written the same command without && or I should have added sudo apt-get install after the &&. So try this:

```

sudo apt-get install libndesk-dbus1.0-cil && sudo gacutil -i /usr/lib/cli/NDesk.DBus-1.0/ NDesk.DBus.dll && sudo gacutil -i /usr/lib/cli/NDesk.DBus.GLib-1.0/NDesk.DBus.GLib.dll

```

I hope that helps and that I haven't made a typo this time:P

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
Also if this doesn't help can you post the terminal output when you execute banshee again?

---

### Post by ddr3XD on 2010-11-12
It still didnt work but i think it shook something.

when i ran banshee in terminal i get a slightly different output than first:

> jayjay@jayjay-desktop:~$ banshee

** (/usr/lib/banshee-1/Banshee.exe:9832): WARNING **: The following assembly referenced from /usr/lib/banshee-1/Banshee.ThickClient.dll could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee-1/).


** (/usr/lib/banshee-1/Banshee.exe:9832): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

** (/usr/lib/banshee-1/Banshee.exe:9832): WARNING **: Missing method AddDefaultFile in assembly /usr/lib/banshee-1/Banshee.ThickClient.dll, type Gtk.Rc

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
File name: 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f'
  at Nereid.Client.Main (System.String[] args) [0x00000] 
  at (wrapper managed-to-native) System.AppDomain:ExecuteAssembly (System.Reflection.Assembly,string[])
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly a, System.String[] args) [0x00000] 
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string,System.Security.Policy.Evidence,string[])
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string)
  at Booter.Booter.BootClient (System.String clientName) [0x00000] 
  at Booter.Booter.Main () [0x00000] 
jayjay@jayjay-desktop:~$ 
I think u almost got it dude. Just try a little more. i have so much faith in you right now. :P

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
Hahahaha! Thank you I must, young Jedi! Maybe this will do the trick for you:

```

sudo gacutil -i /usr/lib/cli/gtk-sharp-2.0/gtk-sharp.dll

```

May the force be with you!

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
Oh, and post the terminal output every time it doesn't work so I can know what's wrong.

---

### Post by ddr3XD on 2010-11-12
installed successfully but still wont start
posting banshee terminal:

> jayjay@jayjay-desktop:~$ banshee

** (/usr/lib/banshee-1/Banshee.exe:9832): WARNING **: The following assembly referenced from /usr/lib/banshee-1/Banshee.ThickClient.dll could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee-1/).


** (/usr/lib/banshee-1/Banshee.exe:9832): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

** (/usr/lib/banshee-1/Banshee.exe:9832): WARNING **: Missing method AddDefaultFile in assembly /usr/lib/banshee-1/Banshee.ThickClient.dll, type Gtk.Rc

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
File name: 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f'
  at Nereid.Client.Main (System.String[] args) [0x00000] 
  at (wrapper managed-to-native) System.AppDomain:ExecuteAssembly (System.Reflection.Assembly,string[])
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly a, System.String[] args) [0x00000] 
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string,System.Security.Policy.Evidence,string[])
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string)
  at Booter.Booter.BootClient (System.String clientName) [0x00000] 
  at Booter.Booter.Main () [0x00000] 
dibbz@boyles-desktop:~$ sudo gacutil -i /usr/lib/cli/gtk-sharp-2.0/gtk-sharp.dll[sudo] password for dibbz: 
Installed /usr/lib/cli/gtk-sharp-2.0/gtk-sharp.dll into the gac (/usr/local/lib/mono/gac)
dibbz@boyles-desktop:~$ banshee
[Info  23:55:08.545] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-10-26 18:21:18 UTC]

** (/usr/lib/banshee-1/Banshee.exe:10021): WARNING **: The following assembly referenced from /usr/local/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll could not be loaded:
     Assembly:   atk-sharp    (assemblyref_index=4)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/local/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/).


** (/usr/lib/banshee-1/Banshee.exe:10021): WARNING **: Could not load file or assembly 'atk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
Stacktrace:

  at Banshee.Gui.GtkBaseClient.Startup<Nereid.Client> () <0xffffffff>
  at Banshee.Gui.GtkBaseClient.Startup<Nereid.Client> () <0x0004e>
  at Banshee.Gui.GtkBaseClient.Startup<Nereid.Client> (string[]) <0x000ca>
  at Nereid.Client.Main (string[]) <0x00015>
  at (wrapper runtime-invoke) Nereid.Client.runtime_invoke_void_object (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x0002b>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00025>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) <0x00019>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0xffffffff>
  at Booter.Booter.BootClient (string) <0x00069>
  at Booter.Booter.Main () <0x00189>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

    banshee-1() [0x80c9774]
    banshee-1() [0x80f5753]
    [0xb772940c]
    banshee-1(mono_class_init+0x569) [0x8176af9]
    banshee-1(mono_class_init+0x803) [0x8176d93]
    banshee-1(mono_class_init+0x803) [0x8176d93]
    banshee-1(mono_class_init+0x803) [0x8176d93]
    banshee-1(mono_class_init+0x803) [0x8176d93]
    banshee-1(mono_class_init+0x803) [0x8176d93]
    banshee-1() [0x807dc17]
    banshee-1() [0x8061698]
    banshee-1() [0x8062e78]
    banshee-1() [0x80d3306]
    [0xb7711066]
    [0xb67d18a3]
    [0xb67d17c6]
    [0xb67d1733]
    banshee-1(mono_runtime_exec_main+0xde) [0x8103e9e]
    [0xb67d16b3]
    [0xb67d159c]
    [0xb67d1476]
    [0xb67d1420]
    [0xb67d13a2]
    [0xb67d1353]
    [0xb67d1172]
    [0xb6fd140a]
    [0xb6fd11fa]
    banshee-1(mono_runtime_exec_main+0xde) [0x8103e9e]
    banshee-1(mono_runtime_run_main+0x15a) [0x810461a]
    banshee-1(mono_main+0x18c4) [0x80b2744]
    banshee-1() [0x805ad75]
    /lib/libc.so.6(__libc_start_main+0xe7) [0xb74a5ce7]
    banshee-1() [0x805acb1]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
jayjay@jayjay-desktop:~$ 
:( I think it got worse

PS: Im going to bed in a while, so if i stop posting back, im probably asleep. :)

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-12
It got almost where it started. I don't get it though. And to think I liked mono. OK, go to sleep and check your mail tomorrow. I'll try to find the answer and post the solution here. Good night!

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
Hey! I forgot to ask you something important: Do you use the 32-bit or the 64-bit version of 10.10? Also, try this:

```

sudo apt-get install --reinstall banshee

```

This will reinstall banshee. If the problem still exists after that I'll find what to do next...

PS: I'm going to take a bath so if it takes me long to reply don't worry...i'm still trying to help! :D

---

### Post by ddr3XD on 2010-11-13
still doesn't start. Im using 32-bit.
here's terminal:

> jayjay@jayjay-desktop:~$ banshee
[Info  19:33:56.091] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-10-26 18:21:18 UTC]

** (/usr/lib/banshee-1/Banshee.exe:4714): WARNING **: The following assembly referenced from /usr/local/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll could not be loaded:
     Assembly:   atk-sharp    (assemblyref_index=4)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/local/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/).


** (/usr/lib/banshee-1/Banshee.exe:4714): WARNING **: Could not load file or assembly 'atk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
Stacktrace:

  at Banshee.Gui.GtkBaseClient.Startup<Nereid.Client> () <0xffffffff>
  at Banshee.Gui.GtkBaseClient.Startup<Nereid.Client> () <0x0004e>
  at Banshee.Gui.GtkBaseClient.Startup<Nereid.Client> (string[]) <0x000ca>
  at Nereid.Client.Main (string[]) <0x00015>
  at (wrapper runtime-invoke) Nereid.Client.runtime_invoke_void_object (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x0002b>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00025>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) <0x00019>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0xffffffff>
  at Booter.Booter.BootClient (string) <0x00069>
  at Booter.Booter.Main () <0x00189>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

    banshee-1() [0x80c9774]
    banshee-1() [0x80f5753]
    [0xb77e640c]
    banshee-1(mono_class_init+0x569) [0x8176af9]
    banshee-1(mono_class_init+0x803) [0x8176d93]
    banshee-1(mono_class_init+0x803) [0x8176d93]
    banshee-1(mono_class_init+0x803) [0x8176d93]
    banshee-1(mono_class_init+0x803) [0x8176d93]
    banshee-1(mono_class_init+0x803) [0x8176d93]
    banshee-1() [0x807dc17]
    banshee-1() [0x8061698]
    banshee-1() [0x8062e78]
    banshee-1() [0x80d3306]
    [0xb77ce066]
    [0xb66e78a3]
    [0xb66e77c6]
    [0xb66e7733]
    banshee-1(mono_runtime_exec_main+0xde) [0x8103e9e]
    [0xb66e76b3]
    [0xb66e759c]
    [0xb66e7476]
    [0xb66e7420]
    [0xb66e73a2]
    [0xb66e7353]
    [0xb66e7172]
    [0xb708e40a]
    [0xb708e1fa]
    banshee-1(mono_runtime_exec_main+0xde) [0x8103e9e]
    banshee-1(mono_runtime_run_main+0x15a) [0x810461a]
    banshee-1(mono_main+0x18c4) [0x80b2744]
    banshee-1() [0x805ad75]
    /lib/libc.so.6(__libc_start_main+0xe7) [0xb7562ce7]
    banshee-1() [0x805acb1]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
jayjay@jayjay-desktop:~$ 

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
Do other mono apps work? For example, have you tried F-Spot or Tomboy Notes?

---

### Post by ddr3XD on 2010-11-13
OMG! F-Spot and Tomboy don't load either. This is a bigger problem than i thought. :(

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
I knew they wouldn't load! Try this on terminal:

```
sudo apt-get install mono-devel
```

I think these are the tools needed to compile mono software. Most likely you'll have them preinstalled but it doesn't hurt trying. Sorry for not being able to help you so far but I wasn't familiar with mono tools and problems like that.

---

### Post by lucifer1 on 2010-11-13
remove it and reinstall and sudo apt-get update befor reinstall it

---

### Post by ddr3XD on 2010-11-13
Crap. I almost thought that would do it...but it didn't XD.None of the mono apps still doesnt start. I even restarted, still nothing. Terminal is the same as last. Should i try to reinstall banshee again now that we messed around with the mono thing? It did download and install a whole bunch of files for the mono.

Just saw your last post. I didn't remove before i reinstalled it. ill try that.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
reinstalling banshee won't help. and mono was screwed up anyway. i'm talking right now on the mono channel

---

### Post by ddr3XD on 2010-11-13
I tried remove before reinstall but that didn't do anything either.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
On the mono channel they pointed me to askubuntu.com. I posted a question there so until they answer it i'll try to work something out myself. Can you tell me how did the problem start? When did you install ubuntu and how (upgrade, fresh installation, as a virtual machine, with wubi.exe)? Also did you do a kernel update or an installation recently? Where you able to run mono apps before?

PS: any useful piece of information you can provide is very well-appreciated!

---

### Post by ddr3XD on 2010-11-13
Aight thanks. I had no idea the problem existed until i installed banshee yesterday and it wouldn't run. then today i found out the mono apps wont start either. I did a clean install of ubuntu about 3 months ago. I don't think i did any kernel updates recently, but i do remember installing kernel updates a while back. One thing i should point out is that about a month ago, somehow i managed to remove Gnome or Nautilus or both. don't ask how. it was a mistake. My computer wouldn't log into my user so i had to run a command:
> sudo apt-get install ubuntu-desktop That did in fact solved the problem. But maybe i ****ed up mono when i ran that command as well. And Yes i was able to run mono apps in the past.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
I'm trying to avoid telling you to remove mono and installing it again. However if we get no answer from askubuntu.com i don't see how we can keep avoiding it. If it comes to this I'll walk you through the whole compilation process. Until then we just wait and see if we can come up with something.

---

### Post by ddr3XD on 2010-11-13
Okay. Ready when you are.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
You mean you want to do it? Are you sure you don't wanna wait for a response from askubuntu.com?

---

### Post by ddr3XD on 2010-11-13
Well, i meant if you didn't get any any response...but look at this thread i found, i think this might do the trick.

[http://ubuntuforums.org/showthread.php?t=658228](http://ubuntuforums.org/showthread.php?t=658228)

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
That's what we're trying to do. But let me first try it on a virtual machine to make sure we don't do anything stupid...

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
Sorry for taking so long to reply but I was installing Ubuntu 10.10 inside Virtualbox and now i'm installing updates to be sure that if a problem comes up is not Ubuntu to blame. After that i'll remove mono and recompile it and then i'll tell you how to do it too. Be patient for a little longer.

---

### Post by ddr3XD on 2010-11-13
> **&#24746 said:**
> Sorry for taking so long to reply but I was installing Ubuntu 10.10 inside Virtualbox and now i'm installing updates to be sure that if a problem comes up is not Ubuntu to blame. After that i'll remove mono and recompile it and then i'll tell you how to do it too. Be patient for a little longer.
Take your time. no worries :guitar:

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
Until I compile it follow this link:

[http://ftp.novell.com/pub/mono/sources-stable/](http://ftp.novell.com/pub/mono/sources-stable/)

and download the first package(the one that says mono-2.8.tar.bz2)

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
Before you try compiling mono just try this:

```
sudo apt-get install --reinstall mono*
```

who knows?it might work...

---

### Post by ddr3XD on 2010-11-13
nope. same terminal output too

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
OK! I won't tell you how to compile it 'cause I removed mono, recompiled it and now I'm having the same problem as you. That's nice though because now I can try it on my pc and if i fix it i can tell you how i did it. Compilation lasted soooooo long that I don't want to put you through it as well:)

---

### Post by ddr3XD on 2010-11-13
Well hopefully u figure it out soon. Best of luck. I'm about to hit the sack again...sooo till' tomorrow buddy and thanks for all the help ;)

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
w8....DON'T GO YET! I worked smth out. w8 for me to post the solution

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
Copy the command inside the text file I attached and paste it in a terminal then hit Enter. That made banshee and f-spot work for me but not tomboy. I hope it works for you too and if it does i'll try tomorrow to find something about tomboy. Don't be intimidated by the command. It's a little amateurish because i was testing and it's so big 'cause I put together many commands.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
I was wrong. Tomboy also worked for me.

---

### Post by ddr3XD on 2010-11-13
:(:(:(:(:(:(
It still doesn't work

I think i got error in term, ill post:
> jayjay@jayjay-desktop:~$ sudo gacutil -i /usr/lib/cli/gtk-sharp-2.0/gtk-sharp.dll && sudo gacutil -i /usr/lib/cli/glib-sharp-2.0/glib-sharp.dll && sudo gacutil -i /usr/lib/cli/atk-sharp-2.0/atk-sharp.dll && sudo gacutil -i /usr/lib/cli/gdk-sharp-2.0/gdk-sharp.dll && sudo gacutil -i /usr/lib/cli/gnome-sharp-2.24/gnome-sharp.dll && sudo gacutil -i /usr/lib/cli/gnome-panel-sharp-2.24/gnome-panel-sharp.dll && sudo gacutil -i /usr/lib/cli/NDesk.DBus-1.0/NDesk.DBus.dll && sudo gacutil -i /usr/lib/cli/NDesk.DBus.GLib-1.0/NDesk.DBus.GLib.dll && sudo gacutil -i /usr/lib/cli/*/* && sudo gacutil -i /usr/lib/cli/launchpad-integration-sharp-1/launchpad-integration-sharp.dll && sudo gacutil -i /usr/lib/cli/**/** && sudo gacutil -i /usr/lib/cli/appindicator-sharp-0.1/appindicator-sharp.dll && sudo gacutil -i /usr/lib/cli/Mono.Addins-0.2/Mono.Addins.dll && sudo gacutil -i /usr/lib/cli/gconf-sharp-2.0/gconf-sharp.dll && sudo gacutil -i /usr/lib/cli/glib-sharp-2.0/glib-sharp.dll && sudo gacutil -i /usr/lib/cli/pango-sharp-2.0/pango-sharp.dll && sudo gacutil -i /usr/lib/cli/gmime-sharp-2.4/gmime-sharp.dll && sudo gacutil -i /usr/lib/cli/Mono.Addins.Setup-0.2/Mono.Addins.Setup.dll && sudo gacutil -i /usr/lib/cli/Mono.Zeroconf-1.0/Mono.Zeroconf.dll
[sudo] password for dibbz: 
Installed /usr/lib/cli/gtk-sharp-2.0/gtk-sharp.dll into the gac (/usr/local/lib/mono/gac)
Installed /usr/lib/cli/glib-sharp-2.0/glib-sharp.dll into the gac (/usr/local/lib/mono/gac)
Installed /usr/lib/cli/atk-sharp-2.0/atk-sharp.dll into the gac (/usr/local/lib/mono/gac)
Installed /usr/lib/cli/gdk-sharp-2.0/gdk-sharp.dll into the gac (/usr/local/lib/mono/gac)
Installed /usr/lib/cli/gnome-sharp-2.24/gnome-sharp.dll into the gac (/usr/local/lib/mono/gac)
Installed /usr/lib/cli/gnome-panel-sharp-2.24/gnome-panel-sharp.dll into the gac (/usr/local/lib/mono/gac)
Installed /usr/lib/cli/NDesk.DBus-1.0/NDesk.DBus.dll into the gac (/usr/local/lib/mono/gac)
Installed /usr/lib/cli/NDesk.DBus.GLib-1.0/NDesk.DBus.GLib.dll into the gac (/usr/local/lib/mono/gac)
Failure adding assembly /usr/lib/cli/appindicator-sharp-0.1/appindicator-sharp.dll/usr/lib/cli/appindicator-sharp-0.1/appindicator-sharp.dll.config/usr/lib/cli/appindicator-sharp-0.1/policy.0.0.appindicator-sharp.config/usr/lib/cli/appindicator-sharp-0.1/policy.0.0.appindicator-sharp.dll/usr/lib/cli/appindicator-sharp-0.1/policy.0.1.appindicator-sharp.config/usr/lib/cli/appindicator-sharp-0.1/policy.0.1.appindicator-sharp.dll/usr/lib/cli/art-sharp-2.0/art-sharp.dll/usr/lib/cli/art-sharp-2.0/art-sharp.dll.config/usr/lib/cli/art-sharp-2.0/policy.2.16.art-sharp.config/usr/lib/cli/art-sharp-2.0/policy.2.16.art-sharp.dll/usr/lib/cli/art-sharp-2.0/policy.2.20.art-sharp.config/usr/lib/cli/art-sharp-2.0/policy.2.20.art-sharp.dll/usr/lib/cli/art-sharp-2.0/policy.2.4.art-sharp.config/usr/lib/cli/art-sharp-2.0/policy.2.4.art-sharp.dll/usr/lib/cli/art-sharp-2.0/policy.2.6.art-sharp.config/usr/lib/cli/art-sharp-2.0/policy.2.6.art-sharp.dll/usr/lib/cli/art-sharp-2.0/policy.2.8.art-sharp.config/usr/lib/cli/art-sharp-2.0/policy.2.8.art-sharp.dll/usr/lib/cli/atk-sharp-2.0/atk-sharp.dll/usr/lib/cli/atk-sharp-2.0/atk-sharp.dll.config/usr/lib/cli/atk-sharp-2.0/libatksharpglue-2.so/usr/lib/cli/FlickrNet-2.2/FlickrNet.dll/usr/lib/cli/gconf-sharp-2.0/gconf-sharp.dll/usr/lib/cli/gconf-sharp-2.0/gconf-sharp.dll.config/usr/lib/cli/gconf-sharp-2.0/policy.2.16.gconf-sharp.config/usr/lib/cli/gconf-sharp-2.0/policy.2.16.gconf-sharp.dll/usr/lib/cli/gconf-sharp-2.0/policy.2.20.gconf-sharp.config/usr/lib/cli/gconf-sharp-2.0/policy.2.20.gconf-sharp.dll/usr/lib/cli/gconf-sharp-2.0/policy.2.4.gconf-sharp.config/usr/lib/cli/gconf-sharp-2.0/policy.2.4.gconf-sharp.dll/usr/lib/cli/gconf-sharp-2.0/policy.2.6.gconf-sharp.config/usr/lib/cli/gconf-sharp-2.0/policy.2.6.gconf-sharp.dll/usr/lib/cli/gconf-sharp-2.0/policy.2.8.gconf-sharp.config/usr/lib/cli/gconf-sharp-2.0/policy.2.8.gconf-sharp.dll/usr/lib/cli/gconf-sharp-peditors-2.24/gconf-sharp-peditors.dll/usr/lib/cli/gdk-sharp-2.0/gdk-sharp.dll/usr/lib/cli/gdk-sharp-2.0/gdk-sharp.dll.config/usr/lib/cli/gdk-sharp-2.0/libgdksharpglue-2.so/usr/lib/cli/gkeyfile-sharp-1.0/gkeyfile-sharp.dll/usr/lib/cli/gkeyfile-sharp-1.0/gkeyfile-sharp.dll.config/usr/lib/cli/glade-sharp-2.0/glade-sharp.dll/usr/lib/cli/glade-sharp-2.0/glade-sharp.dll.config/usr/lib/cli/glade-sharp-2.0/libgladesharpglue-2.so/usr/lib/cli/glib-sharp-2.0/glib-sharp.dll/usr/lib/cli/glib-sharp-2.0/glib-sharp.dll.config/usr/lib/cli/glib-sharp-2.0/libglibsharpglue-2.so/usr/lib/cli/gmime-sharp-2.4/gmime-sharp.dll/usr/lib/cli/gmime-sharp-2.4/gmime-sharp.dll.config/usr/lib/cli/Gnome.Keyring-1.0/Gnome.Keyring.dll/usr/lib/cli/Gnome.Keyring-1.0/Gnome.Keyring.dll.config/usr/lib/cli/Gnome.Keyring-1.0/libgnome-keyring-sharp-glue.so/usr/lib/cli/gnome-panel-sharp-2.24/gnome-panel-sharp.dll/usr/lib/cli/gnome-panel-sharp-2.24/gnome-panel-sharp.dll.config/usr/lib/cli/gnome-panel-sharp-2.24/libgnomepanelsharpglue-2.so/usr/lib/cli/gnome-sharp-2.24/gnome-sharp.dll/usr/lib/cli/gnome-sharp-2.24/gnome-sharp.dll.config/usr/lib/cli/gnome-sharp-2.24/libgnomesharpglue-2.so/usr/lib/cli/gnome-vfs-sharp-2.0/gnome-vfs-sharp.dll/usr/lib/cli/gnome-vfs-sharp-2.0/gnome-vfs-sharp.dll.config/usr/lib/cli/gnome-vfs-sharp-2.0/policy.2.16.gnome-vfs-sharp.config/usr/lib/cli/gnome-vfs-sharp-2.0/policy.2.16.gnome-vfs-sharp.dll/usr/lib/cli/gnome-vfs-sharp-2.0/policy.2.20.gnome-vfs-sharp.config/usr/lib/cli/gnome-vfs-sharp-2.0/policy.2.20.gnome-vfs-sharp.dll/usr/lib/cli/gnome-vfs-sharp-2.0/policy.2.4.gnome-vfs-sharp.config/usr/lib/cli/gnome-vfs-sharp-2.0/policy.2.4.gnome-vfs-sharp.dll/usr/lib/cli/gnome-vfs-sharp-2.0/policy.2.6.gnome-vfs-sharp.config/usr/lib/cli/gnome-vfs-sharp-2.0/policy.2.6.gnome-vfs-sharp.dll/usr/lib/cli/gnome-vfs-sharp-2.0/policy.2.8.gnome-vfs-sharp.config/usr/lib/cli/gnome-vfs-sharp-2.0/policy.2.8.gnome-vfs-sharp.dll/usr/lib/cli/Google.GData.AccessControl-1.4/Google.GData.AccessControl.dll/usr/lib/cli/Google.GData.Apps-1.4/Google.GData.Apps.dll/usr/lib/cli/Google.GData.Blogger-1.4/Google.GData.Blogger.dll/usr/lib/cli/Google.GData.Calendar-1.4/Google.GData.Calendar.dll/usr/lib/cli/Google.GData.Client-1.4/Google.GData.Client.dll/usr/lib/cli/Google.GData.CodeSearch-1.4/Google.GData.CodeSearch.dll/usr/lib/cli/Google.GData.Contacts-1.4/Google.GData.Contacts.dll/usr/lib/cli/Google.GData.Documents-1.4/Google.GData.Documents.dll/usr/lib/cli/Google.GData.Extensions-1.4/Google.GData.Extensions.dll/usr/lib/cli/Google.GData.GoogleBase-1.4/Google.GData.GoogleBase.dll/usr/lib/cli/Google.GData.Health-1.4/Google.GData.Health.dll/usr/lib/cli/Google.GData.Photos-1.4/Google.GData.Photos.dll/usr/lib/cli/Google.GData.Spreadsheets-1.4/Google.GData.Spreadsheets.dll/usr/lib/cli/Google.GData.YouTube-1.4/Google.GData.YouTube.dll/usr/lib/cli/gtk-dotnet-2.0/gtk-dotnet.dll/usr/lib/cli/gtk-dotnet-2.0/gtk-dotnet.dll.config/usr/lib/cli/gtk-sharp-2.0/gtk-sharp.dll/usr/lib/cli/gtk-sharp-2.0/gtk-sharp.dll.config/usr/lib/cli/gtk-sharp-2.0/libgtksharpglue-2.so/usr/lib/cli/gudev-sharp-1.0/gudev-sharp.dll/usr/lib/cli/gudev-sharp-1.0/gudev-sharp.dll.config/usr/lib/cli/indicate-sharp-0.1/indicate-sharp.dll/usr/lib/cli/indicate-sharp-0.1/indicate-sharp.dll.config/usr/lib/cli/launchpad-integration-sharp-1/launchpad-integration-sharp.dll/usr/lib/cli/launchpad-integration-sharp-1/launchpad-integration-sharp.dll.config/usr/lib/cli/Mono.Addins-0.2/Mono.Addins.dll/usr/lib/cli/Mono.Addins-0.2/Mono.Addins.dll.config/usr/lib/cli/Mono.Addins-0.2/policy.0.2.Mono.Addins.config/usr/lib/cli/Mono.Addins-0.2/policy.0.2.Mono.Addins.dll/usr/lib/cli/Mono.Addins-0.2/policy.0.3.Mono.Addins.config/usr/lib/cli/Mono.Addins-0.2/policy.0.3.Mono.Addins.dll/usr/lib/cli/Mono.Addins.CecilReflector-0.2/Mono.Addins.CecilReflector.dll/usr/lib/cli/Mono.Addins.Gui-0.2/Mono.Addins.Gui.dll/usr/lib/cli/Mono.Addins.Gui-0.2/policy.0.2.Mono.Addins.Gui.config/usr/lib/cli/Mono.Addins.Gui-0.2/policy.0.2.Mono.Addins.Gui.dll/usr/lib/cli/Mono.Addins.Gui-0.2/policy.0.3.Mono.Addins.Gui.config/usr/lib/cli/Mono.Addins.Gui-0.2/policy.0.3.Mono.Addins.Gui.dll/usr/lib/cli/Mono.Addins.Setup-0.2/Mono.Addins.Setup.dll/usr/lib/cli/Mono.Addins.Setup-0.2/policy.0.2.Mono.Addins.Setup.config/usr/lib/cli/Mono.Addins.Setup-0.2/policy.0.2.Mono.Addins.Setup.dll/usr/lib/cli/Mono.Addins.Setup-0.2/policy.0.3.Mono.Addins.Setup.config/usr/lib/cli/Mono.Addins.Setup-0.2/policy.0.3.Mono.Addins.Setup.dll/usr/lib/cli/Mono.Zeroconf-1.0/Mono.Zeroconf.dll/usr/lib/cli/Mono.Zeroconf-1.0/Mono.Zeroconf.Providers.AvahiDBus.dll/usr/lib/cli/Mono.Zeroconf-1.0/policy.1.0.config/usr/lib/cli/Mono.Zeroconf-1.0/policy.1.0.Mono.Zeroconf.dll/usr/lib/cli/Mono.Zeroconf-1.0/policy.2.0.config/usr/lib/cli/Mono.Zeroconf-1.0/policy.2.0.Mono.Zeroconf.dll/usr/lib/cli/Mono.Zeroconf-1.0/policy.3.0.config/usr/lib/cli/Mono.Zeroconf-1.0/policy.3.0.Mono.Zeroconf.dll/usr/lib/cli/Mono.Zeroconf-1.0/policy.4.0.config/usr/lib/cli/Mono.Zeroconf-1.0/policy.4.0.Mono.Zeroconf.dll/usr/lib/cli/NDesk.DBus-1.0/NDesk.DBus.dll/usr/lib/cli/NDesk.DBus.GLib-1.0/NDesk.DBus.GLib.dll/usr/lib/cli/NDesk.DBus.GLib-1.0/NDesk.DBus.GLib.dll.config/usr/lib/cli/notify-sharp-0.4/notify-sharp.dll/usr/lib/cli/notify-sharp-0.4/notify-sharp.dll.config/usr/lib/cli/nunit.core-2.4/nunit.core.dll/usr/lib/cli/nunit.core.extensions-2.4/nunit.core.extensions.dll/usr/lib/cli/nunit.core.interfaces-2.4/nunit.core.interfaces.dll/usr/lib/cli/nunit.framework-2.4/nunit.framework.dll/usr/lib/cli/nunit.mocks-2.4/nunit.mocks.dll/usr/lib/cli/nunit.util-2.4/nunit.util.dll/usr/lib/cli/pango-sharp-2.0/libpangosharpglue-2.so/usr/lib/cli/pango-sharp-2.0/pango-sharp.dll/usr/lib/cli/pango-sharp-2.0/pango-sharp.dll.config/usr/lib/cli/taglib-sharp-2.0/policy.2.0.taglib-sharp.config/usr/lib/cli/taglib-sharp-2.0/policy.2.0.taglib-sharp.dll/usr/lib/cli/taglib-sharp-2.0/taglib-sharp.dll to the cache: The system cannot find the file specified.
jayjay@jayjay-desktop:~$ Why does it work on your comp but not mine :confused:
I cant even begin to understand what the crap is goin on here :lolflag:

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
What was the output when running banshee?

---

### Post by ddr3XD on 2010-11-13
> jayjay@jayjay-desktop:~$ banshee
[Info  23:25:48.631] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-10-26 18:21:18 UTC]
[Warn  23:25:49.215] Service `Banshee.Hardware.HardwareManager' not started: No HardwareManager extensions could be loaded. Hardware support will be disabled.
[Warn  23:25:49.217] Caught an exception - System.Exception: No HardwareManager extensions could be loaded. Hardware support will be disabled. (in `Banshee.Services')
  at Banshee.Hardware.HardwareManager..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
[Warn  23:25:49.355] Service `Banshee.Gui.InterfaceActionService' not started: Extension node not found in path: /Banshee/ThickClient/ActionGroup
[Warn  23:25:49.355] Caught an exception - System.InvalidOperationException: Extension node not found in path: /Banshee/ThickClient/ActionGroup (in `Mono.Addins')
  at Mono.Addins.ExtensionContext.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Mono.Addins.AddinManager.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Banshee.Gui.InterfaceActionService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.RegisterService (System.Type type) [0x00000] 

** (Banshee:1653): WARNING **: The following assembly referenced from /usr/lib/banshee-1/Banshee.ThickClient.dll could not be loaded:
     Assembly:   pango-sharp    (assemblyref_index=6)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee-1/).


** (Banshee:1653): WARNING **: Could not load file or assembly 'pango-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.TypeLoadException: A type load exception has occurred.
  at Nereid.PlayerInterface.BuildPrimaryLayout () [0x00000] 
  at Nereid.PlayerInterface.OnShown () [0x00000] 
  at Gtk.Widget.shown_cb (IntPtr widget) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.shown_cb(IntPtr widget)
   at Gtk.Widget.gtk_widget_show(IntPtr )
   at Gtk.Widget.Show()
   at Banshee.Gui.BaseClientWindow.InitialShowPresent()
   at Nereid.PlayerInterface.Initialize()
   at Banshee.Gui.BaseClientWindow.InitializeWindow()
   at Banshee.Gui.BaseClientWindow..ctor(System.String title, System.String configNameSpace, Int32 defaultWidth, Int32 defaultHeight)
   at Nereid.PlayerInterface..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Banshee.ServiceStack.ServiceManager.RegisterService(System.Type type)
   at Banshee.ServiceStack.ServiceManager.Run()
   at Banshee.ServiceStack.Application.Run()
   at Banshee.Gui.GtkBaseClient.Initialize(Boolean registerCommonServices)
   at Banshee.Gui.GtkBaseClient..ctor(Boolean initializeDefault, System.String defaultIconName)
   at Banshee.Gui.GtkBaseClient..ctor()
   at Nereid.Client..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()
jayjay@jayjay-desktop:~$ 
:-k

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
](*,) ```
sudo gacutil -i /usr/lib/cli/pango-sharp-2.0/pango-sharp.dll

```

Crazy staff happens! If that doesn't work post the output again and I'll tell you the solution tomorrow. I already have the next step in case it doesn't work but you have to sleep eventually:D

---

### Post by mc4man on 2010-11-13
I would go into synaptic, search mono and mark mono-runtime, mono-2.0-gac and mono-gac for complete removal - mark each one individually 
You'll lose about 40 or so packages, the list will be saved in file  -> history.

After removing them then browse to /usr/local/lib and see if there is a mono folder, if so  then delete it. (see post 19

Then back in synaptic install banshee and if desired tomboy, gbrainy and any other app that was removed that you want. (apps, not libs, see the list in history.

---

### Post by ddr3XD on 2010-11-13
> jayjay@jayjay-desktop:~$ banshee
[Info  23:35:20.876] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-10-26 18:21:18 UTC]
[Warn  23:35:21.157] Service `Banshee.Hardware.HardwareManager' not started: No HardwareManager extensions could be loaded. Hardware support will be disabled.
[Warn  23:35:21.159] Caught an exception - System.Exception: No HardwareManager extensions could be loaded. Hardware support will be disabled. (in `Banshee.Services')
  at Banshee.Hardware.HardwareManager..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
[Warn  23:35:21.256] Service `Banshee.Gui.InterfaceActionService' not started: Extension node not found in path: /Banshee/ThickClient/ActionGroup
[Warn  23:35:21.256] Caught an exception - System.InvalidOperationException: Extension node not found in path: /Banshee/ThickClient/ActionGroup (in `Mono.Addins')
  at Mono.Addins.ExtensionContext.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Mono.Addins.AddinManager.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Banshee.Gui.InterfaceActionService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.RegisterService (System.Type type) [0x00000] 
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.InvalidOperationException: Extension node not found in path: /Banshee/ThickClient/ContextPane
  at Mono.Addins.ExtensionContext.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Mono.Addins.AddinManager.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Banshee.ContextPane.ContextPageManager..ctor (Banshee.ContextPane.ContextPane pane) [0x00000] 
  at Banshee.ContextPane.ContextPane..ctor () [0x00000] 
  at Nereid.ViewContainer.BuildHeader () [0x00000] 
  at Nereid.ViewContainer..ctor () [0x00000] 
  at Nereid.PlayerInterface.BuildViews () [0x00000] 
  at Nereid.PlayerInterface.BuildPrimaryLayout () [0x00000] 
  at Nereid.PlayerInterface.OnShown () [0x00000] 
  at Gtk.Widget.shown_cb (IntPtr widget) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.shown_cb(IntPtr widget)
   at Gtk.Widget.gtk_widget_show(IntPtr )
   at Gtk.Widget.Show()
   at Banshee.Gui.BaseClientWindow.InitialShowPresent()
   at Nereid.PlayerInterface.Initialize()
   at Banshee.Gui.BaseClientWindow.InitializeWindow()
   at Banshee.Gui.BaseClientWindow..ctor(System.String title, System.String configNameSpace, Int32 defaultWidth, Int32 defaultHeight)
   at Nereid.PlayerInterface..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Banshee.ServiceStack.ServiceManager.RegisterService(System.Type type)
   at Banshee.ServiceStack.ServiceManager.Run()
   at Banshee.ServiceStack.Application.Run()
   at Banshee.Gui.GtkBaseClient.Initialize(Boolean registerCommonServices)
   at Banshee.Gui.GtkBaseClient..ctor(Boolean initializeDefault, System.String defaultIconName)
   at Banshee.Gui.GtkBaseClient..ctor()
   at Nereid.Client..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()
jayjay@jayjay-desktop:~$ still cant run any mono apps. I hope the admins dont get mad at me for pasting all this code. :)

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
I had the same problem I think and I did 
```

sudo gacutil -i /usr/lib/cli/Mono.Addins.Setup-0.2/Mono.Addins.Setup.dll 

```
and fixed it but I'm not sure. I would follow mc4man's advice since I wasn't able to help you so far.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
To be honest i didn't even know that there was a mono-runtime package in synaptic. I feel so stupid sometimes :(  ! I hope mac4man's advice does the trick for you. You can always reinstall the removed packages anyway.

---

### Post by ddr3XD on 2010-11-13
> **&#24746 said:**
> To be honest i didn't even know that there was a mono-runtime package in synaptic. I feel so stupid sometimes :(  ! I hope mac4man's advice does the trick for you. You can always reinstall the removed packages anyway.
First of all don't be so hard on yourself dude. And your saying you haven't been much help but really u have been much help to me. U taught me how to run Banshee from terminal and all kind of other tricks with the terminal.

Second...It still doesn't work. but the error given in terminal when i run banshee has come down to a mere paragraph:
> jayjay@jayjay-desktop:~$ banshee
The assembly mscorlib.dll was not found or could not be loaded.
It should have been installed in the `/usr/local/lib/mono/2.0/mscorlib.dll' directory.
jayjay@jayjay-desktop:~$We have spent a lot of time on this so lets bring it through. Just this last part now. Hopefully its a quick fix.
Oh. and most off all, I made a new friend while trying to fix this. :guitar:

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
Thanks for all the nice things you said! However i'm a little worried that i might screw up things now that you made the problem smaller(there's a better way to say this but it's 6am and i've forgotten my English :D). I think whats missing is on the monodevelop package. Try:

```
sudo apt-get install monodevelop
```

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
Here are all the packages on my system that include the word mono in them. See the attachment.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-11-13
Do this:

```
dpkg -l|grep mono > text.txt
```

That will create a file.txt in your home folder with all the mono packages on your system. If you compared our files you could see what's missing on yours

---

### Post by ddr3XD on 2010-11-13
still same error. maybe mc4man can help us out
ok i'll try items in text file

---

### Post by ddr3XD on 2010-11-14
I'm just about ready to give up. I couldn't do the compare mono apps from the text files thing because there was just too much and they weren't doing anything. I got some help from mc4man. It help with the mscorlib.dll error but now I'm back where I started. I think its time to let this one go. I'll just use Rhythmbox and i rearly use mono apps anyways. To all who helped. thanks for all the help. 

PEACE!!!

PS: By solving the mscorelib.dll error, i did get a slight different terminal than first:
> jayjay@jayjay-desktop:~$ banshee
[Info  11:28:45.122] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-10-26 18:21:18 UTC]
[Warn  11:28:45.442] Service `Banshee.Hardware.HardwareManager' not started: No HardwareManager extensions could be loaded. Hardware support will be disabled.
[Warn  11:28:45.445] Caught an exception - System.Exception: No HardwareManager extensions could be loaded. Hardware support will be disabled. (in `Banshee.Services')
  at Banshee.Hardware.HardwareManager..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
[Warn  11:28:45.537] Service `Banshee.Gui.InterfaceActionService' not started: Extension node not found in path: /Banshee/ThickClient/ActionGroup
[Warn  11:28:45.537] Caught an exception - System.InvalidOperationException: Extension node not found in path: /Banshee/ThickClient/ActionGroup (in `Mono.Addins')
  at Mono.Addins.ExtensionContext.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinManager.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.InterfaceActionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.RegisterService (System.Type type) [0x00000] in <filename unknown>:0 
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.InvalidOperationException: Extension node not found in path: /Banshee/ThickClient/ContextPane
  at Mono.Addins.ExtensionContext.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinManager.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] in <filename unknown>:0 
  at Banshee.ContextPane.ContextPageManager..ctor (Banshee.ContextPane.ContextPane pane) [0x00000] in <filename unknown>:0 
  at Banshee.ContextPane.ContextPane..ctor () [0x00000] in <filename unknown>:0 
  at Nereid.ViewContainer.BuildHeader () [0x00000] in <filename unknown>:0 
  at Nereid.ViewContainer..ctor () [0x00000] in <filename unknown>:0 
  at Nereid.PlayerInterface.BuildViews () [0x00000] in <filename unknown>:0 
  at Nereid.PlayerInterface.BuildPrimaryLayout () [0x00000] in <filename unknown>:0 
  at Nereid.PlayerInterface.OnShown () [0x00000] in <filename unknown>:0 
  at Gtk.Widget.shown_cb (IntPtr widget) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.shown_cb(IntPtr widget)
   at Gtk.Widget.gtk_widget_show(IntPtr )
   at Gtk.Widget.Show()
   at Banshee.Gui.BaseClientWindow.InitialShowPresent()
   at Nereid.PlayerInterface.Initialize()
   at Banshee.Gui.BaseClientWindow.InitializeWindow()
   at Banshee.Gui.BaseClientWindow..ctor(System.String title, System.String configNameSpace, Int32 defaultWidth, Int32 defaultHeight)
   at Nereid.PlayerInterface..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Banshee.ServiceStack.ServiceManager.RegisterService(System.Type type)
   at Banshee.ServiceStack.ServiceManager.Run()
   at Banshee.ServiceStack.Application.Run()
   at Banshee.Gui.GtkBaseClient.Initialize(Boolean registerCommonServices)
   at Banshee.Gui.GtkBaseClient..ctor(Boolean initializeDefault, System.String defaultIconName)
   at Banshee.Gui.GtkBaseClient..ctor()
   at Nereid.Client..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()
jayjay@jayjay-desktop:~$ 


---

### Post by mc4man on 2010-11-14
Well your not really where you started - no more mono errors, banshee is not starting for it's own reasons.

If inclined try this from terminal

```
XLIB_SKIP_ARGB_VISUALS=1 banshee-1
```

or maybe like this may be better from terminal
```
export XLIB_SKIP_ARGB_VISUALS=1 && banshee-1
```

---

### Post by wildabdat on 2011-03-11
thanks guys for the thread specially for @[mc4man]("http://ubuntuforums.org/member.php?u=320715")
i followed the banshee removal on synaptic, then reinstall it, it works for me now :)

:-({|=:-({|=:-({|=:-({|=:-({|=:-({|=

---

