---
title: "Working SA 4250ch firewire program"
date: 2013-06-13
forum: Mythbuntu
---

### Post by bleve on 2013-06-13
All,

I just spent about 2 hours getting firewire to work on my BE to change channels on a Scientific Atlanta 4250HDC Explorer.  There is an excellent post from 2008 in these forums but I had to fumble a bit to get things working.  This is on 12.04 with .26 updates.  After I installed the firewire card I first had to find the 4250 channel changing code which is here:

[http://ubuntuforums.org/showthread.php?t=712789](http://ubuntuforums.org/showthread.php?t=712789)

After I got this code I could not get it to compile as I would get:

> me@myth01:~/src$ cc -std=gnu99 -o 4250ch 4250ch.c -lavc1394 -lrom1394 -lraw1394 
4250ch.c:22:32: fatal error: libavc1394/rom1394.h: No such file or directory

To fix this I ran:

> me@myth01:~/src$  sudo apt-get install build-essential libavc1394-dev libraw1394-dev

After this I was able to compile majoridiot's supplied code but it would not change channels.  Further down in the thread there is a snippet of code from bml137 to send a key release"

> AVC1394_SA3250_OPERAND_KEY_RELEASE

After compiling this I could not get it to work as it was erroring on node0 so I modified one other line to make the starting node be node1.  The complete code is below.  I am posting this so others may save some time getting this to work on their SA4250 STBs:

> /*
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
#define SA4250HD_VENDOR_ID1    0x00001bd7  /* Had to change this for my STB - bleve */
#define SA4250HD_MODEL_ID1    0x000010cc  /* samo's stb */

/* add additional vendor and model id's here- addition needed to if statement starting @ line 134 below */

#define AVC1394_SA3250_COMMAND_CHANNEL 0x000007c00   
#define AVC1394_SA3250_OPERAND_KEY_PRESS 0xe7
#define AVC1394_SA3250_OPERAND_KEY_RELEASE 0x67 

#define CTL_CMD0 AVC1394_CTYPE_CONTROL | AVC1394_SUBUNIT_TYPE_PANEL | \
        AVC1394_SUBUNIT_ID_0 | AVC1394_SA3250_COMMAND_CHANNEL
#define CTL_CMD1 (0x04 << 24)
#define CTL_CMD2 0xff000000

#define STARTING_NODE 1

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

/* add new vendor and model ids    to if stanza below */
    
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
   raw1394_destroy_handle(handle);

   exit(0);
}


---

### Post by bleve on 2013-06-13
I should add, that the code as it was originally written probably will work for many.

---

### Post by one30nav on 2013-06-14
Just to save you some further time and headache: Firewire will jump from node 0 to 1 or from 1 to 0, without notice or reason. So, your next channel change could unexpectedly fail until you either manually select the other node or reboot.

With my Motorola 6200 STB and its associated channel change script (6200ch) that problem was solved ages ago within the script with the introduction of the "-g" GUID switch.

With -g, the channel change script does not look for the node, but the STB's GUID instead.

Good news: It looks like you can get the same functionality for your SA 4250 by using Bradley Corsello's shell script: [http://www.mythtv.org/wiki/Sa4250_ch_guid](http://www.mythtv.org/wiki/Sa4250_ch_guid)

That shell script polls your STB to determine the current node, then pipes that node into sa4250_ch. Pretty cool script.

---

### Post by one30nav on 2013-06-14
Bleve, Also, another way of forcing the use of a specific node vice changing the script code,  is to use, "/usr/bin/sa4250ch -n 1" for the external change command in mythtv's backend setup. Again, not a good idea since Firewire is guaranteed to hop to the other node sooner or later.

---

### Post by bleve on 2013-06-14
"-n" is not in this version of the code. I could add it, but it was quicker for me to just change the first node number.  Maybe I will see if it still changes channels with the error and change the code back.  I will test it tonight.  Figured there was a reason that 6200ch.c had the option.

---

### Post by bleve on 2013-06-14
As the program is now it does not work as non root and gives the following error on node0:
> 
bleve@myth01:~/src$ ./4250ch 3
rom1394_0 warning: read failed: 0x0000fffff0000414
ERROR reading config rom directory for node 0

Attempting to code around this.

---

### Post by bleve on 2013-06-14
Ok, so changed it so it will try both node0 and node1 and not fail if either is not available.  There is probably a better way to do this, as I am not a c programmer and have not written any code of any importance for many many many years:

> /*
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
#define SA4250HD_VENDOR_ID1     0x00001bd7  /* Modified for my stb 4250HDC -bleve */
#define SA4250HD_MODEL_ID1      0x000010cc  /* samo's stb */

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
         perror("ERROR Encountered");
         fprintf(stderr,"ERROR reading config rom directory for node %d error %d\n", i, errno);
  if (errno != 11) {
    raw1394_destroy_handle(handle);
    exit(errno);
  } 
      }

      if (verbose)
         printf("node %d: vendor_id = 0x%08x model_id = 0x%08x\n",
                 i, dir.vendor_id, dir.model_id);

/* add new vendor and model ids to if stanza below */

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
   raw1394_destroy_handle(handle);

   exit(0);



---

### Post by one30nav on 2013-06-14
Just use the link I provided you in my previous post. Bradley Corsello did the work for you and made a sa4250ch.c that takes an "-n" switch.

sudo chmod 777 the resulting sa4250ch and sa4250_guid scripts, throw them in /usr/bin, then you're done.

---

### Post by bleve on 2013-06-14
one30nav, I completely missed that in your post.  I will give it a try.  I agree that is a much better approach.

---

### Post by bleve on 2013-06-14
That is much better, I will modify it so you can pass it the model ID as well so you don't have to recompile it for each model change.  Thanks for the pointer.  It goes to show, sometimes just finding what you need is an issue.

---

