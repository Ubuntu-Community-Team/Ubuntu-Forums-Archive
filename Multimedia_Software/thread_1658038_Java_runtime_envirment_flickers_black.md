---
title: "Java runtime envirment flickers black"
date: 2011-01-02
forum: Multimedia Software
---

### Post by Horomancer on 2011-01-02
Just did a fresh install of 8.04 on wifes laptop (Inspiron 1521) as it has been a nightmare getting things to work with it's hardware and 8.04 seems to have the least issues.
Did the first section of the Comprehensive Multimedia and Video Howto stickied at the top of this forum, then dled minecraft to test things out.

Heres the terminal readout

```
lboo@larry:~/Desktop$ java -jar Minecraft.jar 
java.io.IOException: Cannot run program "javaw": java.io.IOException: error=2, No such file or directory
	at java.lang.ProcessBuilder.start(ProcessBuilder.java:460)
	at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
	at java.lang.UNIXProcess.<init>(UNIXProcess.java:148)
	at java.lang.ProcessImpl.start(ProcessImpl.java:65)
	at java.lang.ProcessBuilder.start(ProcessBuilder.java:453)
	... 1 more
java.io.FileNotFoundException: /home/lboo/.minecraft/lastlogin (No such file or directory)
	at java.io.FileInputStream.open(Native Method)
	at java.io.FileInputStream.<init>(FileInputStream.java:106)
	at net.minecraft.LoginForm.readUsername(LoginForm.java:72)
	at net.minecraft.LoginForm.<init>(LoginForm.java:42)
	at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:20)
	at net.minecraft.LauncherFrame.main(LauncherFrame.java:137)
	at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:36)
Username is 'horomancer'
http://s3.amazonaws.com/MinecraftDownload/lwjgl.jar
http://s3.amazonaws.com/MinecraftDownload/jinput.jar
http://s3.amazonaws.com/MinecraftDownload/lwjgl_util.jar
http://s3.amazonaws.com/MinecraftDownload/minecraft.jar?user=horomancer&ticket=9999ca8c25b6fcc36f3f65df5c7e26f1
http://s3.amazonaws.com/MinecraftDownload/linux_natives.jar.lzma
28
Setting user: horomancer, 4058275030799770954
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event9): Failed to open device /dev/input/event9 (13)

Failed to open device (/dev/input/event8): Failed to open device /dev/input/event8 (13)

Failed to open device (/dev/input/event7): Failed to open device /dev/input/event7 (13)

Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

Player is null
Player is null
Player is now null
99 recipes
Loading texture http://www.minecraft.net/skin/horomancer.png
Player count: 1
Player is bs@2
AL lib: ALc.c:1352: exit(): closing 1 Device
AL lib: ALc.c:1329: alcCloseDevice(): destroying 1 Context
AL lib: alSource.c:2361: alcDestroyContext(): deleting 32 Source(s)
AL lib: alBuffer.c:1081: exit(): deleting 9 Buffer(s)

```

The game runs, but constantly flickers black boxes in the jre window. I've not had this problem before and ran jre and minecraft on other computers without issue. I am using the ATI accelerated proprietary driver.

Any ideas? 
side note- is it possible to set up the .jar file to execute and run in the jre by clicking the icon? My wife wants as little to do in the terminal as possible.

Thanks

---

### Post by Horomancer on 2011-01-02
shameless self bump.

really have no clue on how to get this to work right

---

### Post by unc0nn3ct3d on 2011-09-30
Did you try to turn off visual effects?  System ==> Preferences ==> Appearance ==> Visual Effects, and set it to the top-most option - None.

---

