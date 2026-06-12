---
title: "SA Explorer 4250HDC firewire channel changing support?"
date: 2008-03-02
forum: Mythbuntu
---

### Post by dsbw on 2008-03-02
I've been confused by the number of conflicting things I've read about 4250 firewire channel changing support. I've seen some messages saying it works perfectly without a script, others saying it needs a script, and still others saying it doesn't work at all.

I've got a 4250HDC which I guess is different from the 4250 (has a cable card?) and I'm trying to use it without a channel changing script. It's not working so I've mostly ruled out "works seamlessly without script" (though I could just have a setting wrong). 

Anyone know the definitive answer on this?

---

### Post by majoridiot on 2008-03-04
> **dsbw said:**
> I've been confused by the number of conflicting things I've read about 4250 firewire channel changing support. I've seen some messages saying it works perfectly without a script, others saying it needs a script, and still others saying it doesn't work at all.

I've got a 4250HDC which I guess is different from the 4250 (has a cable card?) and I'm trying to use it without a channel changing script. It's not working so I've mostly ruled out "works seamlessly without script" (though I could just have a setting wrong). 

Anyone know the definitive answer on this?

i ran into this recently while helping someone with a stand-alone changer for their SA4250HD.  i wound up 
modifying the original  mythtv source code and customizing a changer for him that works great.

i'll post the source code for that changer and instructions on how to modify it for your use as soon
as i get home today.  it shouldn't be that difficult. :)

are you trying to change the channel with firewire and record from a tuner input or both change and record
via firewire?

---

### Post by majoridiot on 2008-03-04
ok... here is the source code below is the changer(s) modified for another SA4250HD box... copy and paste the code and save it as **sa4250_ch.c**

```
/*
 * Samo's SA4250HD firewire channel changer by majoridiot
 *
 * requires: libavc1394-dev libraw1394-dev 
 *
 * compile with: gcc -o sa4250_ch sa4250_ch.c -lrom1394 -lavc1394 -lraw1394
 *
 * based on mythtv source code and
 *
 * sa3250ch - an external channel changer for SA3250HD Tuner 
 * Based off 6200ch.c by Stacey D. Son
 * 
 * Copyright 2004,2005 by Stacey D. Son <mythdev@son.org> 
 * Copyright 2005 Matt Porter <mporter@kernel.crashing.org>
 * Portions Copyright 2006 Chris Ingrassia <chris@spicecoffee.org> (SA4200 and Single-digit command mode)
 * 
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software Foundation,
 * Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
 */

#include <libavc1394/rom1394.h>
#include <libavc1394/avc1394.h>
#include <libraw1394/raw1394.h>
#include <sys/types.h>
#include <stdio.h>
#include <errno.h>
#include <stdlib.h>
#include <string.h>

/* SA42xxHD IDs */
#define SA4200HD_VENDOR_ID1     0x000014f8
#define SA4200HD_MODEL_ID1      0x00001072
#define SA4250HD_VENDOR_ID1	0x00001ac3  /* samo's stb */
#define SA4250HD_MODEL_ID1	0x000010cc  /* samo's stb */

/* add additional vendor and model id's here- addition needed to if statement starting @ line 134 below */

#define AVC1394_SA3250_COMMAND_CHANNEL 0x000007c00   
#define AVC1394_SA3250_OPERAND_KEY_PRESS 0xe7
#define AVC1394_SA3250_OPERAND_KEY_RELEASE 0x67 

#define CTL_CMD0 AVC1394_CTYPE_CONTROL | AVC1394_SUBUNIT_TYPE_PANEL | \
        AVC1394_SUBUNIT_ID_0 | AVC1394_SA3250_COMMAND_CHANNEL
#define CTL_CMD1 (0x04 << 24)
#define CTL_CMD2 0xff000000

#define STARTING_NODE 0

void usage()
{
   fprintf(stderr, "Usage: sa_ch [-v] <channel_num>\n");
   fprintf(stderr, "  -v : Verbose Mode\n");
   exit(1);
}

int main (int argc, char *argv[])
{
   rom1394_directory dir;
   int device = -1;
   int single = 0;
   int i;
   int verbose = 0;
   int dig[3];
   int chn = 708;

   if (argc < 2) 
      usage();

  for(i = 1; i < argc; ++i) {
      if ((argv[i][0] == '-') && (strlen(argv[i]) > 1)) {
        switch(argv[i][1]) {
            case 'v':
                verbose = 1;
                break;
            default:
                fprintf(stderr, "WARNING: Unknown option \'%c\', ignoring", argv[i][1]);
        }
      }
      else {
          chn = atoi(argv[i]);
      }
  }

#ifdef RAW1394_V_0_8
   raw1394handle_t handle = raw1394_get_handle();
#else
   raw1394handle_t handle = raw1394_new_handle();
#endif

   if (!handle) {
      if (!errno) {
         fprintf(stderr, "Not Compatible!\n");
      } else {
         perror("Couldn't get 1394 handle");
         fprintf(stderr, "Is ieee1394, driver, and raw1394 loaded?  Are /dev/raw1394 permissions set correctly?\n");
      }
      exit(1);
   } 

   if (raw1394_set_port(handle, 0) < 0) {
      perror("ERROR-- could not set port");
      raw1394_destroy_handle(handle);
      exit(1);
   }

   int nc = raw1394_get_nodecount(handle);
   for (i=STARTING_NODE; i < nc; ++i) {
      if (rom1394_get_directory(handle, i, &dir) < 0) {
         fprintf(stderr,"ERROR reading config rom directory for node %d\n", i);
         raw1394_destroy_handle(handle);
    	 exit(1);
      }

      if (verbose) 
         printf("node %d: vendor_id = 0x%08x model_id = 0x%08x\n", 
                 i, dir.vendor_id, dir.model_id); 

/* add new vendor and model ids	to if stanza below */
	
      if ( ((dir.vendor_id == SA4250HD_VENDOR_ID1) &&
            (dir.model_id == SA4250HD_MODEL_ID1))  || 
	  ((dir.vendor_id == SA4200HD_VENDOR_ID1) &&
	    (dir.model_id == SA4200HD_MODEL_ID1))) { 
            device = i;
            break;
      }
   }
    
   if (device == -1) {
        fprintf(stderr, "Could not find SA42XXHD on the 1394 bus!\n");
	fprintf(stderr, "Try running again with -v and check source code for matching Vendor ID and Model ID-\n");
	fprintf(stderr, "Add if necessary and recompile.\n"); 
        raw1394_destroy_handle(handle);
        exit(1);
   }

   if (verbose)
        printf("Device acquired on node %d\n", device);
        printf("Changing channel %d\n", chn);
        
	quadlet_t cmd[3] =
        {
            CTL_CMD0 | AVC1394_SA3250_OPERAND_KEY_PRESS,
            CTL_CMD1 | (chn << 8),
            CTL_CMD2,
        };        

       if (verbose)
            printf("AV/C Command: cmd0=0x%08x cmd1=0x%08x cmd2=0x%08x\n",
                   cmd[0], cmd[1], cmd[2]);
       avc1394_transaction_block(handle, device, cmd, 3, 1);       

   raw1394_destroy_handle(handle);

   exit(0);
}
```

next, you need to compile it, so install build-essential and the required packages, per the source header comments:

```
$ sudo apt-get install build-essential libavc1394-dev libraw1394-dev
```

next, compile it:

```
$ gcc -o sa4250_ch sa4250_ch.c -lrom1394 -lavc1394 -lraw1394
```

next, see if your box vendor and model id's are familiar to the changer or not... chances are it will not be:

```
$ sudo ./sa2450_ch -v 
```

if you get an error, you will need to add your ids to the source code and recompile.  the previous command, even
if it errored, should have returned the vendor_id and model_id.

add your ids to the source code with the **#defines** at the head.  just for example, we'll assume that the 
vendor_id=0x00001a1a and the model_id=0x00001f1f.  in that case, the first change to the source is here:

```
/* SA42xxHD IDs */
#define SA4200HD_VENDOR_ID1     0x000014f8
#define SA4200HD_MODEL_ID1      0x00001072
#define SA4250HD_VENDOR_ID1	0x00001ac3  /* samo's stb */
#define SA4250HD_MODEL_ID1	0x000010cc  /* samo's stb */

/* add additional vendor and model id's here- addition needed to if statement starting @ line 134 below */
```

add the definitions for your box- e.g.:

```
/* SA42xxHD IDs */
#define SA4200HD_VENDOR_ID1     0x000014f8
#define SA4200HD_MODEL_ID1      0x00001072
#define SA4250HD_VENDOR_ID1	0x00001ac3  /* samo's stb */
#define SA4250HD_MODEL_ID1	0x000010cc  /* samo's stb */
[b]#define SA4250HDC_VENDOR_ID1    0x00001a1a
#define SA4250HDC_MODEL_ID1     0x00001f1f[/b]

/* add additional vendor and model id's here- addition needed to if statement starting @ line 134 below */
```

(making sure to use the correct values for your box)

next, add it into the if stanza as instructed in the source.  it looks like this to begin with:

```
/* add new vendor and model ids	to if stanza below */
	
      if ( ((dir.vendor_id == SA4250HD_VENDOR_ID1) &&
            (dir.model_id == SA4250HD_MODEL_ID1))  || 
	  ((dir.vendor_id == SA4200HD_VENDOR_ID1) &&
	    (dir.model_id == SA4200HD_MODEL_ID1))) { 
            device = i;
            break;
      }
```

and should look like this, when you are done:

```
/* add new vendor and model ids	to if stanza below */
	
      if ( [b]((dir.vendor_id == SA4250HDC_VENDOR_ID1) &&
            (dir.model_id == SA4250HDC_MODEL_ID1))  || [/b]
           ((dir.vendor_id == SA4250HD_VENDOR_ID1) &&
            (dir.model_id == SA4250HD_MODEL_ID1))  || 
	  ((dir.vendor_id == SA4200HD_VENDOR_ID1) &&
	    (dir.model_id == SA4200HD_MODEL_ID1))) { 
            device = i;
            break;
      }
```

then recompile it and test it as above.  once you get it recognized by the changer, test it with:

```
$ sudo ./sa4250_ch channel_number
```

if it changes the channel ok, copy it to /usr/bin:

```
$ sudo cp sa4250_ch /usr/bin
```

and the put sa4250_ch in the correct field for the tuner in backend setup.

---

### Post by dsbw on 2008-03-09
Whoa, thanks! I missed this!

I thought I was going to have to code my own.

I'm planning on using the firewire to change channel but mostly I'll be recording off the regular coax input.

---

### Post by majoridiot on 2008-03-11
the code and procedure has been confirmed as working by another user with an SA4250HDC, so have at it and enjoy! :D

---

### Post by grytpype on 2008-03-28
Thanks for this, you may want to file a ticket with the mythtv folks to get this into their contrib directory for the next release!

---

### Post by majoridiot on 2008-03-29
> **grytpype said:**
> Thanks for this, you may want to file a ticket with the mythtv folks to get this into their contrib directory for the next release!

i sent Jim Westfall (mythtv firewire guru) an email about it and offering the codes for a simple fix... he essentially said "submit a diff for 
a patch".   i'm a bit too wrapped up in fixing the mythbuntu firewire primer for the 8.04 release to dig through the .21 source and make a 
diff... but anyone can feel free to  do so if they want.

if not, i'll try and get to it when i have the time.

---

### Post by dsbw on 2008-03-30
OK, I compile and run, and get this:

```
node 0: vendor_id = 0x00001106 model_id = 0x00000000
node 1: vendor_id = 0x00001ac3 model_id = 0x000010cc
Device acquired on node 1
Changing channel 708

```

So, apparently samo and I have the same STB. The 708 thing is disturbing, though, since that's a PPV channel.

The actual code doesn't seem to do anything however. It just reports that it's "Changing channel n" and the box doesn't change. I ran it verbose:

```
./sa4250_ch -v 4
node 0: vendor_id = 0x00001106 model_id = 0x00000000
node 1: vendor_id = 0x00001ac3 model_id = 0x000010cc
Device acquired on node 1
Changing channel 4
AV/C Command: cmd0=0x00487ce7 cmd1=0x04000400 cmd2=0xff000000

```

:confused:

---

### Post by majoridiot on 2008-03-30
> **dsbw said:**
> OK, I compile and run, and get this:

```
node 0: vendor_id = 0x00001106 model_id = 0x00000000
node 1: vendor_id = 0x00001ac3 model_id = 0x000010cc
Device acquired on node 1
Changing channel 708

```

So, apparently samo and I have the same STB. The 708 thing is disturbing, though, since that's a PPV channel.

The actual code doesn't seem to do anything however. It just reports that it's "Changing channel n" and the box doesn't change. I ran it verbose:

```
./sa4250_ch -v 4
node 0: vendor_id = 0x00001106 model_id = 0x00000000
node 1: vendor_id = 0x00001ac3 model_id = 0x000010cc
Device acquired on node 1
Changing channel 4
AV/C Command: cmd0=0x00487ce7 cmd1=0x04000400 cmd2=0xff000000

```

:confused:

i ran ran into the same issue with samo's box when i worked this out.  as i recall, 
when he changed the firewire bacle to the other port on the etb, it fixed the problem.  
you might try that to see if you get any love.

don't forget to make the cable switch with the pc power off... hotplugging firewire 
isn't generally handled well by the stbs.

---

### Post by bml137 on 2008-08-19
I found a solution.  Mine would not work with Major's changes.  I have the SA 4250HDC.  I was playing around with the code and ran across this and am quite excited.  This may help many and if it does, I hope it will find its way into MythTV.  I don't know the steps to get that done though.

Take Major's code and add the following defines for your 4250HDC...if yours are different, adjust them accordingly.  

```
#define SA4250HDC_VENDOR_ID1    0x00001cea
#define SA4250HDC_MODEL_ID1     0x000010cc
```

Add the HDC defines to the appropriate if statement like below...

```
      if ( ((dir.vendor_id == SA4250HDC_VENDOR_ID1) &&
            (dir.model_id == SA4250HDC_MODEL_ID1)) ||
          ((dir.vendor_id == SA4250HD_VENDOR_ID1) &&
            (dir.model_id == SA4250HD_MODEL_ID1)) ||
          ((dir.vendor_id == SA4200HD_VENDOR_ID1) &&
            (dir.model_id == SA4200HD_MODEL_ID1))) {
            device = i;
            break;
      }
```

Here is the key.  You need to do a "key press" and a "key release".  This is done in the latest MythTV contrib code, but it doesn't work with the 4250HDC for some reason.  It does work when applied to Major's code though.  I don't know why.  Maybe Major knows why.

```
        quadlet_t cmd[3] =
        {
            CTL_CMD0 | AVC1394_SA3250_OPERAND_KEY_PRESS,
            CTL_CMD1 | (chn << 8),
            CTL_CMD2,
        };

       if (verbose)
            printf("AV/C Command: cmd0=0x%08x cmd1=0x%08x cmd2=0x%08x\n",
                   cmd[0], cmd[1], cmd[2]);
       avc1394_transaction_block(handle, device, cmd, 3, 1);

        quadlet_t cmd2[3] =
        {
            CTL_CMD0 | AVC1394_SA3250_OPERAND_KEY_RELEASE,
            CTL_CMD1 | (chn << 8),
            CTL_CMD2,
        };

       if (verbose)
            printf("AV/C Command: cmd0=0x%08x cmd1=0x%08x cmd2=0x%08x\n",
                   cmd2[0], cmd2[1], cmd2[2]);
       avc1394_transaction_block(handle, device, cmd2, 3, 1);
```

Please, let me know if this works.

Brian

---

### Post by majoridiot on 2008-08-19
> **bml137 said:**
> Here is the key.  You need to do a "key press" and a "key release".  This is done in the latest MythTV contrib code, but it doesn't work with the 4250HDC for some reason.  It does work when applied to Major's code though.  I don't know why.  Maybe Major knows why.

Brian

there are two different methods for tuning channels on the 4250HDC- the 
one originally presented here and the one you stumbled across yourself ;)
the one you will need depends entirely on the firmware of the stb.  yours
needed the "alternate" tuning method, which is a key_release at the end, as
you found.

the info probably should have been posted sooner, but there's only so much
time in the day... plus, figuring it out yourself was much more valuable i'm sure.

you might check out the newest version of the mythprime primer and see if the
channel-changer built in there will work with your stb.  my guess is you will need 
to force the 4250HDC alternate changer (-f 4) for it to work.

glad you got it working and the info is now posted!

---

### Post by bml137 on 2008-08-19
What is the mythprime primer?  I assume that is different than the trunk version of the sa3250_ch contrib.

---

### Post by majoridiot on 2008-08-19
> **bml137 said:**
> What is the mythprime primer?  I assume that is different than the trunk version of the sa3250_ch contrib.

[http://ubuntuforums.org/showthread.php?t=884880](http://ubuntuforums.org/showthread.php?t=884880)

you might also want to look at:

[http://ubuntuforums.org/showthread.php?t=795378](http://ubuntuforums.org/showthread.php?t=795378)

sources for both are at:

[https://wiki.ubuntu.com/majoridiot](https://wiki.ubuntu.com/majoridiot)

---

### Post by bml137 on 2008-08-20
mythprime does not appear to work for me.  Using it raw, it did not work because "-f 4" was being changed to "-f 2" in the code.  I commented out that line and it is able to change the channel.

However, the P2P connection keeps reporting:
```
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
```

I think these "receiving packets" things were working before in some other program.  I will have try again after I restart the computer.

---

### Post by htpcfan on 2008-09-07
I have tried using both mythprime ([http://ubuntuforums.org/showthread.php?t=884880](http://ubuntuforums.org/showthread.php?t=884880)) and the method in this thread and I still cannot get my SA4250hdc to change channels. 

I get the following output with mythprime but still no channel change. (The STB was on channel 1 and I ran both:
```
sudo -v -c 5
sudo -v -f 4 -c 5
```

I also made sure that the code replacing the changer 4 was commented out.The output is the same for both commands above):

> 
mythprime .69a beta

Acquiring firewire handle... OK.
1 port(s) found

Acquiring handle on port 0... 1 devices detected.
Skipping empty node 0
STB Vendor ID: 0x1cea Model ID: 0x10cc, Scientific Atlanta Model SA4250HDC

(Using user selected channel changer #4)

1 STB(s) found:
-------------
STB 1: port=0, node=1, p2p=1, changer=4, GUID=0x001ceae668d20000

Priming STB 1:
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... 59 packets received
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... 32 packets received
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... 84 packets received
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... 163 packets received
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... 76 packets received
Disconnecting P2P connection on node 1, channel 1
Successfully primed stb on port 1 node 2.



Also to note, if the STB is not on channel 1 the receiving packets fails. Any help with this will be really appreciated as this is all really new to me.

---

### Post by RDV on 2008-11-11
Using the code that originated from this post ([http://www.gossamer-threads.com/lists/mythtv/users/346598](http://www.gossamer-threads.com/lists/mythtv/users/346598)), I can change channels on my sa8300HD PVR. 

I would like to add to the code the equivalent of the pvr's remotes "select" key after the channel number is entered. The problem is I do not know the hex code for the "select" key. 

The reason I want to add the "select" key code is that the channel change is immediate and the pvr does not display an overlay on the video which indicates the channel. This overlay ends up being captured during recording and has to be edited out, sometimes chopping out part of the program I am recording.

Does anyone know what the "select" hex key code is or how I can find it for the sa8300HD pvr?

I suspect that it is the same hex code for at least the sa3250, sa4350, sa8000 and their HD equivalents. 

Anyones help would be greatly appreciated.

---

### Post by jerunamuck on 2009-01-25
Thanks Major, this is working where the IR fails on my SA4300HD.  FYI:

#define SA4300HD_VENDOR_ID1	0x00001E6B
#define SA4300HD_MODEL_ID1	0x000010CC

Also, I had to chmod +s on the executable to get this to work.

Funny thing, scan does not seem to use this but view TV does.
That is, when scanning channels the cable box never changes channels but when attempting to watch live tv the channels do change.  Perhaps this is already fixed in a later version.  Hopefully upgrading from 7.10 this weekend will not break the channel changer now that it's working.... Dooh!

---

### Post by bml137 on 2009-04-01
The pulling of video has seemed to stop working again.  It stopped working a couple days ago after I did a typical update.  Today, to try and fix it, I upgraded to 9.04.  The problem was not resolved.

I am able to change channels.  'mythprime', including Major's 69h version, are unable to communicate at all.  The 'sa4250_ch' I made edits to a few months ago (documented earlier in this thread) is able to change channels.

My guess is the internal MythTV stuff was changed which blocked my firmware.  Anyone recently have this happen?

---

### Post by LowSky on 2010-07-15
Does this still work with newer verisions, I would love to try this

---

