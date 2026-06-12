---
title: "DVD Drive speed"
date: 2007-10-26
forum: Mythbuntu
---

### Post by yfaykya on 2007-10-26
Hi all,
I was using feisty with SVN and the DVD drive slowed down when playing DVDs so DVDs were watchable. I upgraded to mythbuntu (disabled the standard mythfronend/backend) and now the DVD drive will not slow down. I tried the packaged frontend but no joy there either. Any ideas? Its making watching a DVD impossible.

PS. I tried hdparam -E, eject -x and setcd -x and none worked. Thanks,

D.

---

### Post by superm1 on 2007-10-28
I've never heard of such a necessity.  Do you know why this is necessary in the first place?

---

### Post by yfaykya on 2007-10-29
I don't understand your question. Why what is necessary?

---

### Post by yfaykya on 2007-10-29
If you mean why slowing the DVD drive down its because of the noise. It is VERY loud at full speed. It is done automatically in myth in the setSpeed function in mythcdrom-linux.cpp (in SVN anyway). This does not seem to work anymore. I suspect something may have changed in the kernel but not sure.

---

### Post by jb5 on 2007-11-06
Bump:

Hi - I am also looking for a solution to this.

At the moment I have a Samsung S203 20x DVDRW / SATA Drive which spins up to full speed when inserting and playing a DVD. This makes the drive far too noisy to ignore while viewing a film.

I would like to reduce the read speed whilst playing DVD in order to quieten the drive noise.

Maybe through the DVD launch command in MythTV?

---

### Post by yfaykya on 2007-11-13
I have it sorted by doing the following in /etc/rc.local

/usr/local/bin/speedcontrol -x 2 /dev/dvd

You might want to add user to /etc/fstab for your dvd device.

The code for speedcontrol : 

/*
 * SpeedControl - use SET STREAMING command to set the speed of DVD-drives
 *       
 *
 * Copyright (c) 2004   Thomas Fritzsche <tf@noto.de>
 *
 *   This program is free software; you can redistribute it and/or modify
 *   it under the terms of the GNU General Public License as published by
 *   the Free Software Foundation; either version 2 of the License, or
 *   (at your option) any later version.
 *
 *   This program is distributed in the hope that it will be useful,
 *   but WITHOUT ANY WARRANTY; without even the implied warranty of
 *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *   GNU General Public License for more details.
 *
 *   You should have received a copy of the GNU General Public License
 *   along with this program; if not, write to the Free Software
 *   Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
 *
 */

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <string.h>
#include <unistd.h>
#include <sys/ioctl.h>
#include <linux/cdrom.h>

 
void dump_sense(unsigned char *cdb, struct request_sense *sense)
{
  int i;
  
  printf("Command failed: ");
    
  for (i=0; i<12; i++)
    printf("%02x ", cdb[i]);
          
    if (sense) {
      printf(" - sense: %02x.%02x.%02x\n", sense->sense_key, sense->asc,
              sense->ascq);
    } else {
      printf(", no sense\n");
    }
}

int main(int argc, char *argv[])
{
  char *device = "/dev/cdrom";
  int c,fd;
  int speed = 0;
  unsigned long rw_size;
  
  unsigned char buffer[28];
  
  struct cdrom_generic_command cgc;
  struct request_sense sense;
  extern char * optarg;

  while((c=getopt(argc,argv,"x:"))!=EOF) {
    switch(c) {
      case 'x': speed = atoi(optarg); break;
      default:
        printf("Usage: speedcontrol [-x speed] [device]");
        return -1;
    }
  }

  if (argc > optind) device = argv[optind];
  
  fd = open(device, O_RDONLY | O_NONBLOCK);
  if (fd < 0) {
    printf("Can't open device %s\n", device);
    return -1;
  }


  memset(&cgc, 0, sizeof(cgc));
  memset(&sense, 0, sizeof(sense));
  memset(&buffer, 0, sizeof(buffer));

 /* SET STREAMING command */ 
  cgc.cmd[0] = 0xb6;
 /* 28 byte parameter list length */
  cgc.cmd[10] = 28; 

  cgc.sense = &sense;
  cgc.buffer = buffer;
  cgc.buflen = sizeof(buffer);
  cgc.data_direction = CGC_DATA_WRITE;
  cgc.quiet = 1;
  
  if(speed == 0) {
/* set Restore Drive Defaults */  
    buffer[0] = 4;
  }

  buffer[8] = 0xff;
  buffer[9] = 0xff;
  buffer[10] = 0xff;
  buffer[11] = 0xff;

  rw_size = 177 * speed;

/* read size */  
  buffer[12] = (rw_size >> 24) & 0xff;
  buffer[13] = (rw_size >> 16) & 0xff;
  buffer[14] = (rw_size >>  8) & 0xff;
  buffer[15] = rw_size & 0xff;

/* read time 1 sec. */
  buffer[18] = 0x03;
  buffer[19] = 0xE8;

/* write size */
  buffer[20] = (rw_size >> 24) & 0xff;
  buffer[21] = (rw_size >> 16) & 0xff;
  buffer[22] = (rw_size >>  8) & 0xff;
  buffer[23] = rw_size & 0xff;

/* write time 1 sec. */
  buffer[26] = 0x03;
  buffer[27] = 0xE8;
 
  if (ioctl(fd, CDROM_SEND_PACKET, &cgc) != 0)       
    if (ioctl(fd, CDROM_SELECT_SPEED, speed) != 0) {
      dump_sense(cgc.cmd, cgc.sense);    
      printf("ERROR.\n");
      return -1;
    }
  printf("OK...\n");
  return 0;
}

---

### Post by jb5 on 2007-11-14
Hi - Nice find, thank you for posting.  :KS

I copied the program to /usr/local/bin/speedcontrol.c

I replaced the smilies with 8 followed by )

then :-

```
cd /usr/local/bin
sudo chmod 774 speedcontrol.c
sudo gcc speedcontrol.c
sudo cp a.out speedcontrol

```

Seems to have done the trick, thank you again.

EDIT ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
OK, it nearly works!
I am attempting to play my DVD through MythTV.
So If I load the DVD, then open a terminal and enter ```
speedcontrol -x 2 /dev/dvd
```
AND THEN try to play the DVD it will play at 2x speed.

If I bypass the *speedcontrol* command it plays at full speed.

I have noticed that rc.local is run when the machine is shutting down, is it supposed to run during both statrtup & shutdown?

EDIT 2
In Myth Frontend, if I go to setup - media settings - dvd settings - play settings - There is a box to enter a command to start playing the dvd.

I am struggling to find the right format to enter the following sequence
/usr/local/bin/speedcontrol -x 2 /dev/dvd
followed by 
Internal
To start playing the DVD.
I've tried enclosing the speedcontrol part in "..." ; '...'; or leaving it as a bare command.
I've tried to separate the speedcontrol command and Internal command with | ; & ; &&
none of which seem to work.

Anybody any bright ideas? I hope it's something very simple!

---

### Post by jb5 on 2007-12-12
OK - Maybe there isn't a one click solution.

The best compromise I've found is to assign the command to a button on my remote (see [MythTV](http://parker1.co.uk/mythtv_ubuntu2.php) or [nova_t_500](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Remote_control) for example), or create a button on a desktop panel that runs the command if not using remote/mythTV.

So in my .mythtv/lircrc file I have the following section

```
#	Radio
##	Slows DVD read speed
begin
prog = irexec
button = Radio
config = sudo /usr/local/bin/speedcontrol -x 2 /dev/dvd
end
```

I have also added /usr/local/bin/speedcontrol to my sudoers file

```
sudo visudo
``````
# user mythtv can reduce read speed of DVD drive
%mythtv ALL = NOPASSWD: /usr/local/bin/speedcontrol

```


Now all I have to do is hit the Radio button before playing my DVD and the read speed is reduced. I need to do this every time I mount the DVD, as running the command at boot/login didn't appear to work for me (YMMV). 
Also this didn't appear to work until after a reboot.

---

### Post by axelsvag on 2007-12-22
Does not anyone have found a more automatic solution yet. Can it really be so dificult since it worked in Feisty at least at my setup?

---

### Post by jdeslip on 2009-01-30
Sorry to bring up such an old thread, but I have the same problem on mythbuntu 8.10 - DVD drive is loud when watching a dvd.  Did anyone ever find a way to automatically run speedcontrol when playing a DVD?  (The remote irexec work around isn't very ideal).

---

### Post by axelsvag on 2009-01-31
There is one drive speed menu in mythbuntu 8.04. I think it came with the mythtv 0,21. Have you tried to use that?

---

### Post by jdeslip on 2009-01-31
Perhaps I am just blind, but where do you see this setting?

---

### Post by axelsvag on 2009-02-01
OK, on my system i find it here. I made the translation from swedish so it can be that the menus have somewhat different name on your system

1. Tools/setting
2. Settings
3. Media
4. Video
5. Generic
6. Generic settings 3/7

There is a settings that looks like it can  change the drive speed.

---

### Post by ariodante on 2009-02-11
Is there a solution for this for Ubuntu Hardy?  Preferably one that loads at boot time or with the DVD playing software?  It is odd that this should be so difficult to fix.

---

### Post by jdeslip on 2009-02-11
Sorry, I forgot to reply.  But the setting axelsvag mentioned doesn't currently work because of a bug. 

It is reported here for mythtv:  

[http://www.gossamer-threads.com/lists/mythtv/commits/363716](http://www.gossamer-threads.com/lists/mythtv/commits/363716)

And here for mythbuntu:

[https://bugs.launchpad.net/mythbuntu/+bug/312444](https://bugs.launchpad.net/mythbuntu/+bug/312444)

It seems the package was accepted into trunk and may make 0.21-fixes soon.  Perhaps, we can inquire there as to if it has made it in, yet...

---

