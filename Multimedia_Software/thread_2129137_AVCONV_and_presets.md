---
title: "AVCONV and presets"
date: 2013-03-25
forum: Multimedia Software
---

### Post by FizzBuntu on 2013-03-25
Hi

I'm using AVCONV to convert videos. Nothing really complex, but i'd like to put my parameters in a preset file so that I'd have to state the input/output file and which preset.
But the documentation as only a few lines on presets and most of the options used in the command line wont work as is.
I might ad that the few presets found in the /usr/share/avconv are useless.

My command line is : 
avconv -i MyInuputFile -s 960x540 -vcodec libx264 -acodec libmp3lame -b:v 3000k -b:a 192k MyOutputFile

Any ideas ?

---

### Post by evilsoup on 2013-03-25
The preset files are really more for when you have a load of really complex options, and they're applied on a per-codec basis. In your case, I don't think they'd shorten your command line by any useful amount.

I think the easiest way to achieve what you want would be a bash script.

```

#!/bin/bash
avconv -i "$1" -s 960x540 -vcodec libx264 -acodec libmp3lame -b:v 3000k -b:a 192k "$2"
exit 0

```

This takes advantage of [positional parameters](http://www.linuxcommand.org/wss0130.php). Save it as 'my_avconv' somewhere in your $PATH (like ~/bin) and set it as executable, and then use it like this:

```

my_avconv input.file output.file

```

As usual, quote file names with spaces.

---

