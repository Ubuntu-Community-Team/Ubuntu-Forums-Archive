---
title: "Amarok acting up"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by teamkiller87 on 2007-11-27
After i removed and reinstalled some ruby libraries in an attempt to make ruby work last night i busted amarok. Each time it switches to another song it gives me the following error:

The script 'Default' exited with error code: 1

/usr/share/apps/amarok/scripts/score_default/score_default.rb:9:in `require': no such file to load -- uri (LoadError)
from /usr/share/apps/amarok/scripts/score_default/score_default.rb:9

I know I must have removed the wrong library but I obviously can't remember which one... The music plays just fine but getting an error every time it switches to the next song is really bugging. HELP?!

---

### Post by zabbaskeema on 2007-12-02
BUMP!
Damn.

---

### Post by zabbaskeema on 2007-12-02
Ok, I have a workaround.
This will effectively disable the scoring capability of Amarok but I coulndt careless. :-)

```
cp -p /usr/share/apps/amarok/scripts/score_default/score_default.rb  /usr/share/apps/amarok/scripts/score_default/score_default.rb.bak
```


```
vi  /usr/share/apps/amarok/scripts/score_default/score_default.rb
```

Replace content by:

```
#!/usr/bin/env ruby
#
# Amarok Script for custom scoring
#
# (c) 2006 Gábor Lehel <illissius@gmail.com>
#
# License: GNU General Public License V2


loop do
    args = gets.chomp.split(" ")

    case args[0]
        when "configure"
            msg  = 'This script does not require any configuration.'
            `dcop amarok playlist popupMessage "#{msg}"`

        when "requestNewScore"
    end
end
```


Cheers, 

Pat

---

