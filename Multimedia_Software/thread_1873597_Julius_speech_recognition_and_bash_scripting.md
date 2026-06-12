---
title: "Julius speech recognition and bash scripting"
date: 2011-11-01
forum: Multimedia Software
---

### Post by kkaldroma on 2011-11-01
I have julius working and have made my own grammar files, the speech to text aspect is working just fine.
my issue is passing that text to a bash script so it can execute code.
I see that this can be done with python but I don't know python.

I either need a python script that will accept the text string and send it to the bash script or to have Julius pass the string as plain text and close...

I'm dying here.

---

### Post by kkaldroma on 2011-11-29
Python is a bitch to learn from forum examples but I pulled it off. Figured I should share my results for the next poor guy.
```

#! /usr/bin/python -u

import sys
import os

from subprocess import call

class CommandAndControl:

    def __init__(self, file_object):

        startstring = 'sentence1: <s> '
        endstring = ' </s>'

        while 1:
            line = file_object.readline()
            if not line:
                break
            if line.startswith(startstring) and line.strip().endswith(endstring):
                self.parse(line.strip('\n')[len(startstring):-len(endstring)])

    def parse(self, line):
        # Parse the input
        params = [param.lower() for param in line.split() if param]
        if not '-q' in sys.argv and not '--quiet' in sys.argv:
            stdin_var= ' '.join(params).capitalize()
#            print stdin_var
            call("LINK TO BASH SCRIPT" + stdin_var, shell=True)        
if __name__ == '__main__':
    try:
        CommandAndControl(sys.stdin)
    except KeyboardInterrupt:
        sys.exit(1)

```

---

### Post by rivera151 on 2012-09-11
Hey, nice job. It seems you hacked python in about a month, got what you wanted and shared it.

I had been watching the julius project for years now and was surprised to see than Ubuntu now has the julius and julius-voxforge packages.

You have a language model? Is it in english? Would/could you be willing to share that? I think both this little script of yours and the language model would essentially have the basic framework for speech-to-text to be fully usable/reusable in linux by others wishing to interface with it.

I hope this stuff makes it upstream...

---

### Post by gbrowning on 2012-11-12
I am having trouble getting started with Julius.  Just do not know where to begin.  Is there a tutorial or a HOW -TO you can point out?

---

### Post by gbrowning on 2012-11-13
Finally found the information I needed in the Voxforge site and in the documents incuded in their "quickstart" downloads.

---

### Post by gbrowning on 2012-11-26
Though I have gone through as much of the Julius literature as I can understand I am getting stuck without starting Julius.
     I get a segmentation error (core dumped) when I try to start the program.  the problem seems to be part of the input.  The configuration file sets "-input mic" to /dev/dsp  which should work but does not.
     diagnosis attempt
    [I] $ pacmd list-sources | grep alsa_input 
    name: <alsa_input.usb-HP_HP_Webcam_3100-02-H3100.analog-mono>
    name: <alsa_input.pci-0000_00_1b.0.analog-stereo>[/I]

     reading through the configuration file there is a way to specify an audio input device but I have not been able to figure out how to do it.  It says 
[I]#-input mic             # direct microphone input
            # device name can be specified via env. val. "AUDIODEV"[/I]

Please set me straight

---

