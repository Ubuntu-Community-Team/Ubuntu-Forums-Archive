---
title: "OSS Patch in Swiftfox problems"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by chriswyatt on 2007-06-25
Basically, the Macromedia Flash plugin keeps crashing my Firefox.  It occasionally happens if I go to another page when a flash video is playing or if I try and close Firefox if a video is playing, there is a solution here:

[https://help.ubuntu.com/community/RestrictedFormats/Flash#head-f036b17c3150dd72f58d952a0e13094568c9f92e](https://help.ubuntu.com/community/RestrictedFormats/Flash#head-f036b17c3150dd72f58d952a0e13094568c9f92e)

I followed the solution but can't get the Swiftfox patch to work, I get this error message:

```
Hunk #1 FAILED at 163.
1 out of 1 hunk FAILED -- saving rejects to file /usr/lib/swiftfox/run-mozilla.sh.rej
```

Here are the contents of run-mozilla.sh.rej:

```
***************
*** 163,169 ****
         ##
         ## Run the program
         ##
-        "$prog" ${1+"$@"}
         exitcode=$?
         if [ "$DEBUG_CORE_FILES" ]
         then
--- 163,192 ----
         ##
         ## Run the program
         ##
+        if [ -f /etc/firefox/firefoxrc ]; then
+            . /etc/firefox/firefoxrc
+        fi
+        if [ -z "${FIREFOX_DSP}" ]; then
+            #FIREFOX_DSP="auto"
+            FIREFOX_DSP="none"
+            # esddsp is dreadful, see https://launchpad.net/malone/bugs/29760
+        fi
+        ##
+        ## find /dev/dsp handler
+        ##
+ 
+        if [ "${FIREFOX_DSP}" = "auto" ]; then
+            FIREFOX_DSP=
+            if pgrep -u         d -u esd >/dev/null 2>&1; then
+                FIREFOX_DSP=esddsp
+            elif pgrep -u       d -u arts >/dev/null 2>&1; then
+                FIREFOX_DSP=artsdsp
+            fi
+        elif [ "${FIREFOX_DSP}" = "none" ]; then
+            FIREFOX_DSP=
+        fi
+ 
+        exec "${FIREFOX_DSP}" "$prog" ${1+"$@"}
         exitcode=$?
         if [ "$DEBUG_CORE_FILES" ]
         then
```

Could this be because the solution is for an older version of Swiftfox?  I've been putting up with the crashing until now but I'd really like to get this fixed.

---

### Post by chriswyatt on 2007-06-29
Bump

---

