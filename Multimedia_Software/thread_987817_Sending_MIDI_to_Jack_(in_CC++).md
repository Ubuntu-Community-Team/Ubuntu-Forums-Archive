---
title: "Sending MIDI to Jack (in C/C++)"
date: 2008-11-19
forum: Multimedia Software
---

### Post by redxine on 2008-11-19
I am attempting to write a program that will take the input of (Say a guitar hero controller) and send the appropriate MIDI notes to JACK. I've tried using the midiio library, but the application never shows up as a JACK client. The QJackctl client window flashes as if it's refreshing, but nothing happens. I tried using their example program:

```
//
// Programmer:    Craig Stuart Sapp <craig@ccrma.stanford.edu>
// Creation Date: Sat Nov  2 20:29:03 PST 2002
// Last Modified: Fri Mar 14 07:32:13 PST 2003
// Filename:      midiouttest.cpp
// Syntax:        ANSI C++; midiio 1.0
//
// Description:   Test program to make sure that MIDI output is working.
//

#include "midiiolib.h"
#include <iostream>
using namespace std;

int main(void) {
   Voice output;
   output.setPort(1);   // choose which port you want to sent MIDI out on.
   output.open();       // not necessary for all OS configurations but best
                        // to always use the open command.
                        // output.setAndOpenPort(0) can also be used.
   int i;
   for (i=0; i<100; i++) {
      cout << "Playing Note " << i << " ..." << endl;
      output.play(0, 60, 64);               // play a Middle C MIDI note
      millisleep(250);                      // pause for 250 milliseconds
   }

   output.close();      // port will close automatically when exiting the 
                        // program (normally) if not explicitly closed.

   return 0;
}

```

Any help would be appreciated.

---

