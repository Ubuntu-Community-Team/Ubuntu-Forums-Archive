---
title: "sa4250_ch_guid : an improved SA4250 channel changer for multiple STBs"
date: 2008-04-15
forum: Mythbuntu
---

### Post by grytpype on 2008-04-15
Hello all...

My Myth setup includes two SA4250HD STBs, which I control using Firewire.  I've been using MajorIdiot's sa4250_ch channel changing program, but found it didn't handle multiple STBs well, so I modified it a bit.

My new setup has a shell wrapper, sa4250_ch_guid, and a modified version of Major's channel changer, sa4250_ch_new, that is in C and needs to be compiled as per Major's instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=712789](http://ubuntuforums.org/showthread.php?t=712789)

To use, put both the wrapper and channel changer in /usr/local/bin, and invoke sa4250_ch_guid with the GUID of the box you want to control and the channel as parameters.  You don't need the whole GUID, just enough of it to be a unique search key (there is no checking of this so make sure you have it right).

sa4250_ch_guid determines the node number of the STB with the given GUID and passes that as a parameter to sa4250_ch_new.  This is necessary because node numbers often seem to change at unpredictable times.

sa4250_ch_guid

```
#!/bin/sh
#
# sa4250_ch_guid
#

GUID="$1"
CHANNEL="$2"

/usr/local/bin/sa4250_ch_new -n $(plugreport 2>/dev/null | awk '/'$GUID'/ {print $2}' - ) $CHANNEL

```

sa4250_ch_new.c

```
/*
 * Samo's SA4250HD firewire channel changer by majoridiot
 *
 * modified by grytpype to take node number as a parameter
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
#define SA4250HD_VENDOR_ID1	0x00001cea  /* samo's stb */
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
   fprintf(stderr, "Usage: sa4250_ch_new [-v] [-n <node>] <channel_num>\n");
   fprintf(stderr, "  -v : Verbose Mode\n");
   fprintf(stderr, "  -p : Node to change - default 0\n");
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
   int unode = 0;

   if (argc < 2) 
      usage();

  for(i = 1; i < argc; ++i) {
      if ((argv[i][0] == '-') && (strlen(argv[i]) > 1)) {
        switch(argv[i][1]) {
            case 'v':
                verbose = 1;
                break;
            case 's':
                single = 1;

                break;
            case 'n':
                unode = atoi(argv[++i]);
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
/*  for (i=unode; i < unode; ++i) {   */
      if (rom1394_get_directory(handle, unode, &dir) < 0) {
         fprintf(stderr,"ERROR reading config rom directory for node %d\n", unode);
         raw1394_destroy_handle(handle);
    	 exit(1);
      }

      if (verbose) 
         printf("node %d: vendor_id = 0x%08x model_id = 0x%08x\n", 
                 unode, dir.vendor_id, dir.model_id); 

/* add new vendor and model ids	to if stanza below */
	
      if ( ((dir.vendor_id == SA4250HD_VENDOR_ID1) &&
            (dir.model_id == SA4250HD_MODEL_ID1))  || 
	  ((dir.vendor_id == SA4200HD_VENDOR_ID1) &&
	    (dir.model_id == SA4200HD_MODEL_ID1))) { 
            device = unode;
/*            break;  */
      }
/*   }   */
    
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

---

### Post by bic on 2008-10-28
hmmm, suddenly, my SA4250 channel changer stopped working.  It's been running fine since April.  I am able to do a  test-mpeg2 -r 1 > test.mpg and play it back with sound and video.

I tried compiling newer sa4250_ch above and setting up the script:

node 1: vendor_id = 0x00001ac3 model_id = 0x000010cc
Device acquired on node 1
Changing channel 2
AV/C Command: cmd0=0x00487ce7 cmd1=0x04000200 cmd2=0xff000000


Existing sa4250_ch

sa4250_ch 2 -v
node 0: vendor_id = 0x000090a9 model_id = 0x00000000
node 1: vendor_id = 0x00001ac3 model_id = 0x000010cc
Device acquired on node 1
Changing channel 2
AV/C Command: cmd0=0x00487ce7 cmd1=0x04000200 cmd2=0xff000000


Nothing happens on the display of the STB.  I tried switching firewire on STB, but this didn't help either.  I also unplugged STB power and restarted it.  This didn't help.  Anything else I can try?

---

### Post by bic on 2008-10-28
I just went through the 33 page menu on STB and found 0x0002DE as vendor id, model is 0x000010cc.  I tried recompiling with this, but get 

node 0: vendor_id = 0x000090a9 model_id = 0x00000000
Could not find SA42XXHD on the 1394 bus!
Try running again with -v and check source code for matching Vendor ID and Model ID-
Add if necessary and recompile.

Various software had dates of August of 2008. I suspect something got updated on the STB that hosed the channel changer script.

---

