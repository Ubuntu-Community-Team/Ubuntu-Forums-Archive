---
title: "bash-completion problems"
date: 2010-05-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zika on 2010-05-27
On start of gnome-terminal I get:```
bash: /etc/bash_completion.d/apt: line 32: syntax error near unexpected token `;'
bash: /etc/bash_completion.d/apt: line 32: `                    2> /dev/null ); $( apt-cache --no-generate pkgnames "lib$cur" \'
bash: /etc/bash_completion.d/apt: line 33: syntax error near unexpected token `)'
bash: /etc/bash_completion.d/apt: line 33: `                    2> /dev/null); )
```
I'll try to see what's wrong but...

---

### Post by Vanishing on 2010-05-27
> **zika said:**
> On start of gnome-terminal I get:```
bash: /etc/bash_completion.d/apt: line 32: syntax error near unexpected token `;'
bash: /etc/bash_completion.d/apt: line 32: `                    2> /dev/null ); $( apt-cache --no-generate pkgnames "lib$cur" \'
bash: /etc/bash_completion.d/apt: line 33: syntax error near unexpected token `)'
bash: /etc/bash_completion.d/apt: line 33: `                    2> /dev/null); )
```
I'll try to see what's wrong but...

Confirm. Exact same problem...
Some fun in maverick now.

---

### Post by Loxx on 2010-05-27
getting this too

---

### Post by MacUntu on 2010-05-27
****Removing the two ";" seems to work, but I'm not feeling very comfortable doing this.

---

### Post by wayneericgouin on 2010-05-27
Yes, first came the gnome-terminal removal, then after I fixed that I now have this bash error as well.

---

### Post by ronacc on 2010-05-27
it was the upgrade to bash-completion 1.1.1-3ubuntu3 that did it I started gnome-terminal no errors then upgraded and started it again and the errors are there . anyone bug it yet ?

---

### Post by MacUntu on 2010-05-27
> **ronacc said:**
> anyone bug it yet ?

The bad patch points to this bug: [https://bugs.launchpad.net/ubuntu/+source/bash-completion/+bug/546794](https://bugs.launchpad.net/ubuntu/+source/bash-completion/+bug/546794)

---

### Post by ronacc on 2010-05-27
looks like they're on it last post says they are going to revert the patch .

---

### Post by zika on 2010-05-29
I've got some spare time on my hands, played with offending file and got the results I've wrote on launchpad, in that bug report...
My opinion is that, now with two ";" removed it works as it is supposed to work, even though I think that, now, without ";" syntax is not 20/20...

---

### Post by Reiger on 2010-05-29
Why not? The statement in question seems to be an array and ( AAA BBB CCC )  is a perfectly valid array declaration syntax?

---

### Post by zika on 2010-05-29
> **Reiger said:**
> Why not? The statement in question seems to be an array and ( AAA BBB CCC )  is a perfectly valid array declaration syntax?Then, we are OK just with removing 2 ";"...

---

### Post by xeizo on 2010-05-29
I removed them, but I'm left with "enexpected end of file" which I can't seem to do anything about. Everything works though, it's just that it's plain ugly when opening the CLI.

---

### Post by Reiger on 2010-05-29
> **xeizo said:**
> I removed them, but I'm left with "enexpected end of file" which I can't seem to do anything about. Everything works though, it's just that it's plain ugly when opening the CLI.

Well you must have removed something more than or different from those two semi-colons in the outer parentheses (on line 33). 
That error means there's an opening statement somewhere but not a corresponding closing statement (e.g. opening parenthesis without matching closing parenthesis).

My version of /etc/bash_completion.d/apt is this:
```

# Debian apt-get(8) completion.

have apt-get &&
_apt_get()
{
    local cur prev special i
/etc/bas
    COMPREPLY=()
    cur=`_get_cword`
    prev=${COMP_WORDS[COMP_CWORD-1]}

    for (( i=0; i < ${#COMP_WORDS[@]}-1; i++ )); do
        if [[ ${COMP_WORDS[i]} == @(install|remove|autoremove|purge|source|build-dep) ]]; then
            special=${COMP_WORDS[i]}
        fi
    done

    if [ -n "$special" ]; then
        case $special in
            remove|autoremove|purge)
                if [ -f /etc/debian_version ]; then
                    # Debian system
                    COMPREPLY=( $( _comp_dpkg_installed_packages $cur ) )
                else
                    # assume RPM based
                    _rpm_installed_packages
                fi
                return 0
                ;;
            *)
                COMPREPLY=( $( apt-cache --no-generate pkgnames "$cur" \
                    2> /dev/null ) $( apt-cache --no-generate pkgnames "lib$cur" \
                    2> /dev/null) )
                return 0
                ;;
        esac
    fi

    case "$prev" in
        -@(c|-config-file))
             _filedir
             return 0
             ;;
        -@(t|-target-release|-default-release))
             COMPREPLY=( $( apt-cache policy | \
                 grep "release.o=Debian,a=$cur" | \
                 sed -e "s/.*a=\(\w*\).*/\1/" | uniq 2> /dev/null) )
             return 0
             ;;
    esac

    if [[ "$cur" == -* ]]; then
        COMPREPLY=( $( compgen -W '-d -f -h -v -m -q -s -y -u -t -b -c -o \
            --download-only --fix-broken --help --version --ignore-missing \
            --fix-missing --no-download --quiet --simulate --just-print \
            --dry-run --recon --no-act --yes --assume-yes --show-upgraded \
            --only-source --compile --build --ignore-hold --target-release \
            --no-upgrade --force-yes --print-uris --purge --reinstall \
            --list-cleanup --default-release --trivial-only --no-remove \
            --diff-only --no-install-recommends --tar-only --config-file \
            --option --auto-remove' -- "$cur" ) )
    else
        COMPREPLY=( $( compgen -W 'update upgrade dselect-upgrade \
            dist-upgrade install remove purge source build-dep \
            check clean autoclean autoremove' -- "$cur" ) )
    fi

    return 0
} &&
complete -F _apt_get $filenames apt-get

# Debian apt-cache(8) completion.
#
have apt-cache &&
_apt_cache()
{
    local cur prev special i

    COMPREPLY=()
    cur=`_get_cword`
    prev=${COMP_WORDS[COMP_CWORD-1]}


    if [ "$cur" != show ]; then
        for (( i=0; i < ${#COMP_WORDS[@]}-1; i++ )); do
        if [[ ${COMP_WORDS[i]} == @(add|depends|dotty|madison|policy|rdepends|show?(pkg|src|)) ]]; then
            special=${COMP_WORDS[i]}
        fi
        done
    fi


    if [ -n "$special" ]; then
        case $special in
        add)
            _filedir
            return 0
            ;;

        showsrc)
            COMPREPLY=( $( apt-cache dumpavail | \
                            grep "^Source: $cur" | sort | \
                            uniq | cut -f2 -d" " ) )
            return 0
            ;;

        *)
            COMPREPLY=( $( apt-cache --no-generate pkgnames "$cur" 2> /dev/null ) )
            return 0
            ;;

        esac
    fi


    case "$prev" in
         -@(c|p|s|-config-file|-@(pkg|src)-cache))
             _filedir
             return 0
             ;;
         search)
             if [[ "$cur" != -* ]]; then
                return 0
             fi
             ;;
    esac

    if [[ "$cur" == -* ]]; then

        COMPREPLY=( $( compgen -W '-h -v -p -s -q -i -f -a -g -c \
                -o --help --version --pkg-cache --src-cache \
                --quiet --important --full --all-versions \
                --no-all-versions --generate --no-generate \
                --names-only --all-names --recurse \
                --config-file --option --installed' -- "$cur" ) )
    else

        COMPREPLY=( $( compgen -W 'add gencaches show showpkg showsrc \
                stats dump dumpavail unmet search search \
                depends rdepends pkgnames dotty xvcg \
                policy madison' -- "$cur" ) )

    fi


    return 0
} &&
complete -F _apt_cache $filenames apt-cache

# Local variables:
# mode: shell-script
# sh-basic-offset: 4
# sh-indent-comment: t
# indent-tabs-mode: nil
# End:
# ex: ts=4 sw=4 et filetype=sh


```

---

### Post by ronacc on 2010-05-29
> **Reiger said:**
> Well you must have removed something more than or different from those two semi-colons in the outer parentheses (on line 33). 
That error means there's an opening statement somewhere but not a corresponding closing statement (e.g. opening parenthesis without matching closing parenthesis).

My version of /etc/bash_completion.d/apt is this:
```

# Debian apt-get(8) completion.

have apt-get &&
_apt_get()
{
    local cur prev special i
/etc/bas
    COMPREPLY=()
    cur=`_get_cword`
    prev=${COMP_WORDS[COMP_CWORD-1]}

    for (( i=0; i < ${#COMP_WORDS[@]}-1; i++ )); do
        if [[ ${COMP_WORDS[i]} == @(install|remove|autoremove|purge|source|build-dep) ]]; then
            special=${COMP_WORDS[i]}
        fi
    done

    if [ -n "$special" ]; then
        case $special in
            remove|autoremove|purge)
                if [ -f /etc/debian_version ]; then
                    # Debian system
                    COMPREPLY=( $( _comp_dpkg_installed_packages $cur ) )
                else
                    # assume RPM based
                    _rpm_installed_packages
                fi
                return 0
                ;;
            *)
                COMPREPLY=( $( apt-cache --no-generate pkgnames "$cur" \
                    2> /dev/null ) $( apt-cache --no-generate pkgnames "lib$cur" \
                    2> /dev/null) )
                return 0
                ;;
        esac
    fi

    case "$prev" in
        -@(c|-config-file))
             _filedir
             return 0
             ;;
        -@(t|-target-release|-default-release))
             COMPREPLY=( $( apt-cache policy | \
                 grep "release.o=Debian,a=$cur" | \
                 sed -e "s/.*a=\(\w*\).*/\1/" | uniq 2> /dev/null) )
             return 0
             ;;
    esac

    if [[ "$cur" == -* ]]; then
        COMPREPLY=( $( compgen -W '-d -f -h -v -m -q -s -y -u -t -b -c -o \
            --download-only --fix-broken --help --version --ignore-missing \
            --fix-missing --no-download --quiet --simulate --just-print \
            --dry-run --recon --no-act --yes --assume-yes --show-upgraded \
            --only-source --compile --build --ignore-hold --target-release \
            --no-upgrade --force-yes --print-uris --purge --reinstall \
            --list-cleanup --default-release --trivial-only --no-remove \
            --diff-only --no-install-recommends --tar-only --config-file \
            --option --auto-remove' -- "$cur" ) )
    else
        COMPREPLY=( $( compgen -W 'update upgrade dselect-upgrade \
            dist-upgrade install remove purge source build-dep \
            check clean autoclean autoremove' -- "$cur" ) )
    fi

    return 0
} &&
complete -F _apt_get $filenames apt-get

# Debian apt-cache(8) completion.
#
have apt-cache &&
_apt_cache()
{
    local cur prev special i

    COMPREPLY=()
    cur=`_get_cword`
    prev=${COMP_WORDS[COMP_CWORD-1]}


    if [ "$cur" != show ]; then
        for (( i=0; i < ${#COMP_WORDS[@]}-1; i++ )); do
        if [[ ${COMP_WORDS[i]} == @(add|depends|dotty|madison|policy|rdepends|show?(pkg|src|)) ]]; then
            special=${COMP_WORDS[i]}
        fi
        done
    fi


    if [ -n "$special" ]; then
        case $special in
        add)
            _filedir
            return 0
            ;;

        showsrc)
            COMPREPLY=( $( apt-cache dumpavail | \
                            grep "^Source: $cur" | sort | \
                            uniq | cut -f2 -d" " ) )
            return 0
            ;;

        *)
            COMPREPLY=( $( apt-cache --no-generate pkgnames "$cur" 2> /dev/null ) )
            return 0
            ;;

        esac
    fi


    case "$prev" in
         -@(c|p|s|-config-file|-@(pkg|src)-cache))
             _filedir
             return 0
             ;;
         search)
             if [[ "$cur" != -* ]]; then
                return 0
             fi
             ;;
    esac

    if [[ "$cur" == -* ]]; then

        COMPREPLY=( $( compgen -W '-h -v -p -s -q -i -f -a -g -c \
                -o --help --version --pkg-cache --src-cache \
                --quiet --important --full --all-versions \
                --no-all-versions --generate --no-generate \
                --names-only --all-names --recurse \
                --config-file --option --installed' -- "$cur" ) )
    else

        COMPREPLY=( $( compgen -W 'add gencaches show showpkg showsrc \
                stats dump dumpavail unmet search search \
                depends rdepends pkgnames dotty xvcg \
                policy madison' -- "$cur" ) )

    fi


    return 0
} &&
complete -F _apt_cache $filenames apt-cache

# Local variables:
# mode: shell-script
# sh-basic-offset: 4
# sh-indent-comment: t
# indent-tabs-mode: nil
# End:
# ex: ts=4 sw=4 et filetype=sh


```

I renamed /etc/bash_completion.d/apt and cut and pasted your version there 
still getting

```
bash: /etc/bash_completion.d/apto: line 32: syntax error near unexpected token `;'
bash: /etc/bash_completion.d/apto: line 32: `                    2> /dev/null ); $( apt-cache --no-generate pkgnames "lib$cur" \'
bash: /etc/bash_completion.d/apto: line 33: syntax error near unexpected token `)'
bash: /etc/bash_completion.d/apto: line 33: `                    2> /dev/null); )'
ron@ron-desktop2:~$ 
```

note I even tried rebooting to see maybe it loaded that at startup .

---

### Post by vigstrom on 2010-05-29
> **ronacc said:**
> I renamed /etc/bash_completion.d/apt and cut and pasted your version there 
still getting

```
bash: /etc/bash_completion.d/apto: line 32: syntax error near unexpected token `;'
bash: /etc/bash_completion.d/apto: line 32: `                    2> /dev/null ); $( apt-cache --no-generate pkgnames "lib$cur" \'
bash: /etc/bash_completion.d/apto: line 33: syntax error near unexpected token `)'
bash: /etc/bash_completion.d/apto: line 33: `                    2> /dev/null); )'
ron@ron-desktop2:~$ 
```

note I even tried rebooting to see maybe it loaded that at startup .

Hmm, you left the renamed file in /etc/bash_completion.d/
everything in that folder will be read. Move the file "apto" somewhere else.

---

### Post by zika on 2010-05-29
Here is the file I've got after aforementioned surgery...
.txt is just to bypass filter...

---

### Post by ronacc on 2010-05-29
> **vigstrom said:**
> Hmm, you left the renamed file in /etc/bash_completion.d/
everything in that folder will be read. Move the file "apto" somewhere else.

thanks I didn't notice that it was reading apto I'll move it .

@ zika I'll also try the file you posted  thanks .

Got to run off right now I'll report back later .

---

### Post by zika on 2010-05-29
> **ronacc said:**
> @ zika I'll also try the file you posted  thanks.Do not follow me, I do not know, either, the correct path through this wood... :)

---

### Post by ronacc on 2010-05-29
not to worry , I backup a file before I edit it . Thats where the apto referenced above came from , o for original :D besides I have lots of practice recovering from self inflicted wounds , see my sig :lolflag:

---

### Post by xeizo on 2010-05-29
@ Reiger; I probably did, your file works fine! Thanks!

---

### Post by ronacc on 2010-05-29
both Zika's and Reiger's apt's work , they are identical as far as I can tell .

---

### Post by zika on 2010-05-30
> **ronacc said:**
> not to worry , I backup a file before I edit it . Thats where the apto referenced above came from , o for original :D besides I have lots of practice recovering from self inflicted wounds , see my sig :lolflag:I do quote Your sig, at least, a couple of dozen of times during each and every week... :)

---

### Post by crjackson on 2010-05-31
Is anyone else getting this when invoking a terminal cli?

```
bash: /etc/bash_completion.d/apt: line 32: syntax error near unexpected token `;'
bash: /etc/bash_completion.d/apt: line 32: `                    2> /dev/null ); $( apt-cache --no-generate pkgnames "lib$cur" \'
bash: /etc/bash_completion.d/apt: line 33: syntax error near unexpected token `)'
bash: /etc/bash_completion.d/apt: line 33: `                    2> /dev/null); )'
xxxxxx@emachines-laptop:~$
```

---

### Post by go7Ul1ai on 2010-05-31
I am also getting this

---

### Post by zika on 2010-05-31
"Solved" at [http://ubuntuforums.org/showthread.php?t=1494962](http://ubuntuforums.org/showthread.php?t=1494962)

---

### Post by Penguin Guy on 2010-05-31
I've attached a patch that should fix the problem, just [download it]("http://ubuntuforums.org/attachment.php?attachmentid=158906&d=1275327707") and run this:
```
sudo patch /etc/bash_completion.d/apt **/path/to/**apt_completion.txt
```
*(it's a [FONT="Courier New"].txt[/FONT] to bypass the file filter)*

---

### Post by zika on 2010-05-31
> **Penguin Guy said:**
> I've attached a patch that should fix the problem, just download it and run this:
```
sudo patch /etc/bash_completion.d/apt **/path/to/**apt_completion.txt
```
*(it's a [FONT="Courier New"].txt[/FONT] to bypass the file filter)*I was curious. After using Your patch I get, again```
bash: /etc/bash_completion.d/apt: line 34: syntax error near unexpected token `;;'
bash: /etc/bash_completion.d/apt: line 34: `                ;;'
bash: /etc/bash_completion.d/apt: line 35: syntax error near unexpected token `esac'
bash: /etc/bash_completion.d/apt: line 35: `        esac'
```
Maybe it would be good idea if You could send correct /etc/bash_comletion.d/apt to see what does correct file look like...

---

### Post by zika on 2010-05-31
Taking some time to look at the bug and file itself, maybe file attached is a better bet...

---

### Post by crjackson on 2010-05-31
> **Reiger said:**
> Well you must have removed something more than or different from those two semi-colons in the outer parentheses (on line 33). 
That error means there's an opening statement somewhere but not a corresponding closing statement (e.g. opening parenthesis without matching closing parenthesis).

My version of /etc/bash_completion.d/apt is this:
```

# Debian apt-get(8) completion.

have apt-get &&
_apt_get()
{
    local cur prev special i
/etc/bas
    COMPREPLY=()
    cur=`_get_cword`
    prev=${COMP_WORDS[COMP_CWORD-1]}

    for (( i=0; i < ${#COMP_WORDS[@]}-1; i++ )); do
        if [[ ${COMP_WORDS[i]} == @(install|remove|autoremove|purge|source|build-dep) ]]; then
            special=${COMP_WORDS[i]}
        fi
    done

    if [ -n "$special" ]; then
        case $special in
            remove|autoremove|purge)
                if [ -f /etc/debian_version ]; then
                    # Debian system
                    COMPREPLY=( $( _comp_dpkg_installed_packages $cur ) )
                else
                    # assume RPM based
                    _rpm_installed_packages
                fi
                return 0
                ;;
            *)
                COMPREPLY=( $( apt-cache --no-generate pkgnames "$cur" \
                    2> /dev/null ) $( apt-cache --no-generate pkgnames "lib$cur" \
                    2> /dev/null) )
                return 0
                ;;
        esac
    fi

    case "$prev" in
        -@(c|-config-file))
             _filedir
             return 0
             ;;
        -@(t|-target-release|-default-release))
             COMPREPLY=( $( apt-cache policy | \
                 grep "release.o=Debian,a=$cur" | \
                 sed -e "s/.*a=\(\w*\).*/\1/" | uniq 2> /dev/null) )
             return 0
             ;;
    esac

    if [[ "$cur" == -* ]]; then
        COMPREPLY=( $( compgen -W '-d -f -h -v -m -q -s -y -u -t -b -c -o \
            --download-only --fix-broken --help --version --ignore-missing \
            --fix-missing --no-download --quiet --simulate --just-print \
            --dry-run --recon --no-act --yes --assume-yes --show-upgraded \
            --only-source --compile --build --ignore-hold --target-release \
            --no-upgrade --force-yes --print-uris --purge --reinstall \
            --list-cleanup --default-release --trivial-only --no-remove \
            --diff-only --no-install-recommends --tar-only --config-file \
            --option --auto-remove' -- "$cur" ) )
    else
        COMPREPLY=( $( compgen -W 'update upgrade dselect-upgrade \
            dist-upgrade install remove purge source build-dep \
            check clean autoclean autoremove' -- "$cur" ) )
    fi

    return 0
} &&
complete -F _apt_get $filenames apt-get

# Debian apt-cache(8) completion.
#
have apt-cache &&
_apt_cache()
{
    local cur prev special i

    COMPREPLY=()
    cur=`_get_cword`
    prev=${COMP_WORDS[COMP_CWORD-1]}


    if [ "$cur" != show ]; then
        for (( i=0; i < ${#COMP_WORDS[@]}-1; i++ )); do
        if [[ ${COMP_WORDS[i]} == @(add|depends|dotty|madison|policy|rdepends|show?(pkg|src|)) ]]; then
            special=${COMP_WORDS[i]}
        fi
        done
    fi


    if [ -n "$special" ]; then
        case $special in
        add)
            _filedir
            return 0
            ;;

        showsrc)
            COMPREPLY=( $( apt-cache dumpavail | \
                            grep "^Source: $cur" | sort | \
                            uniq | cut -f2 -d" " ) )
            return 0
            ;;

        *)
            COMPREPLY=( $( apt-cache --no-generate pkgnames "$cur" 2> /dev/null ) )
            return 0
            ;;

        esac
    fi


    case "$prev" in
         -@(c|p|s|-config-file|-@(pkg|src)-cache))
             _filedir
             return 0
             ;;
         search)
             if [[ "$cur" != -* ]]; then
                return 0
             fi
             ;;
    esac

    if [[ "$cur" == -* ]]; then

        COMPREPLY=( $( compgen -W '-h -v -p -s -q -i -f -a -g -c \
                -o --help --version --pkg-cache --src-cache \
                --quiet --important --full --all-versions \
                --no-all-versions --generate --no-generate \
                --names-only --all-names --recurse \
                --config-file --option --installed' -- "$cur" ) )
    else

        COMPREPLY=( $( compgen -W 'add gencaches show showpkg showsrc \
                stats dump dumpavail unmet search search \
                depends rdepends pkgnames dotty xvcg \
                policy madison' -- "$cur" ) )

    fi


    return 0
} &&
complete -F _apt_cache $filenames apt-cache

# Local variables:
# mode: shell-script
# sh-basic-offset: 4
# sh-indent-comment: t
# indent-tabs-mode: nil
# End:
# ex: ts=4 sw=4 et filetype=sh


```

I pasted the contents of your file OVER my old apt file and it seems to work just fine now.  Thanks.

---

### Post by crjackson on 2010-05-31
> **zika said:**
> "Solved" at [http://ubuntuforums.org/showthread.php?t=1494962](http://ubuntuforums.org/showthread.php?t=1494962)

Thanks, this worked for me.

---

### Post by zika on 2010-05-31
> **Reiger said:**
> Well you must have removed something more than or different from those two semi-colons in the outer parentheses (on line 33). 
That error means there's an opening statement somewhere but not a corresponding closing statement (e.g. opening parenthesis without matching closing parenthesis).

My version of /etc/bash_completion.d/apt is this:
```

# Debian apt-get(8) completion.

have apt-get &&
_apt_get()
{
    local cur prev special i
[COLOR="Red"]/etc/bas[/COLOR]
    COMPREPLY=()
    cur=`_get_cword`
    prev=${COMP_WORDS[COMP_CWORD-1]}

    for (( i=0; i < ${#COMP_WORDS[@]}-1; i++ )); do
        if [[ ${COMP_WORDS[i]} == @(install|remove|autoremove|purge|source|build-dep) ]]; then
            special=${COMP_WORDS[i]}
        fi
    done

    if [ -n "$special" ]; then
        case $special in
            remove|autoremove|purge)
                if [ -f /etc/debian_version ]; then
                    # Debian system
                    COMPREPLY=( $( _comp_dpkg_installed_packages $cur ) )
                else
                    # assume RPM based
                    _rpm_installed_packages
                fi
                return 0
                ;;
            *)
                COMPREPLY=( $( apt-cache --no-generate pkgnames "$cur" \
                    2> /dev/null ) $( apt-cache --no-generate pkgnames "lib$cur" \
                    2> /dev/null) )
                return 0
                ;;
        esac
    fi

    case "$prev" in
        -@(c|-config-file))
             _filedir
             return 0
             ;;
        -@(t|-target-release|-default-release))
             COMPREPLY=( $( apt-cache policy | \
                 grep "release.o=Debian,a=$cur" | \
                 sed -e "s/.*a=\(\w*\).*/\1/" | uniq 2> /dev/null) )
             return 0
             ;;
    esac

    if [[ "$cur" == -* ]]; then
        COMPREPLY=( $( compgen -W '-d -f -h -v -m -q -s -y -u -t -b -c -o \
            --download-only --fix-broken --help --version --ignore-missing \
            --fix-missing --no-download --quiet --simulate --just-print \
            --dry-run --recon --no-act --yes --assume-yes --show-upgraded \
            --only-source --compile --build --ignore-hold --target-release \
            --no-upgrade --force-yes --print-uris --purge --reinstall \
            --list-cleanup --default-release --trivial-only --no-remove \
            --diff-only --no-install-recommends --tar-only --config-file \
            --option --auto-remove' -- "$cur" ) )
    else
        COMPREPLY=( $( compgen -W 'update upgrade dselect-upgrade \
            dist-upgrade install remove purge source build-dep \
            check clean autoclean autoremove' -- "$cur" ) )
    fi

    return 0
} &&
complete -F _apt_get $filenames apt-get

# Debian apt-cache(8) completion.
#
have apt-cache &&
_apt_cache()
{
    local cur prev special i

    COMPREPLY=()
    cur=`_get_cword`
    prev=${COMP_WORDS[COMP_CWORD-1]}


    if [ "$cur" != show ]; then
        for (( i=0; i < ${#COMP_WORDS[@]}-1; i++ )); do
        if [[ ${COMP_WORDS[i]} == @(add|depends|dotty|madison|policy|rdepends|show?(pkg|src|)) ]]; then
            special=${COMP_WORDS[i]}
        fi
        done
    fi


    if [ -n "$special" ]; then
        case $special in
        add)
            _filedir
            return 0
            ;;

        showsrc)
            COMPREPLY=( $( apt-cache dumpavail | \
                            grep "^Source: $cur" | sort | \
                            uniq | cut -f2 -d" " ) )
            return 0
            ;;

        *)
            COMPREPLY=( $( apt-cache --no-generate pkgnames "$cur" 2> /dev/null ) )
            return 0
            ;;

        esac
    fi


    case "$prev" in
         -@(c|p|s|-config-file|-@(pkg|src)-cache))
             _filedir
             return 0
             ;;
         search)
             if [[ "$cur" != -* ]]; then
                return 0
             fi
             ;;
    esac

    if [[ "$cur" == -* ]]; then

        COMPREPLY=( $( compgen -W '-h -v -p -s -q -i -f -a -g -c \
                -o --help --version --pkg-cache --src-cache \
                --quiet --important --full --all-versions \
                --no-all-versions --generate --no-generate \
                --names-only --all-names --recurse \
                --config-file --option --installed' -- "$cur" ) )
    else

        COMPREPLY=( $( compgen -W 'add gencaches show showpkg showsrc \
                stats dump dumpavail unmet search search \
                depends rdepends pkgnames dotty xvcg \
                policy madison' -- "$cur" ) )

    fi


    return 0
} &&
complete -F _apt_cache $filenames apt-cache

# Local variables:
# mode: shell-script
# sh-basic-offset: 4
# sh-indent-comment: t
# indent-tabs-mode: nil
# End:
# ex: ts=4 sw=4 et filetype=sh


```The only thing for which I can not see why it is there is **/etc/bas** in the very beginning... :) That is the only diff between Your file and my "previous" file, before this "new" one, above... as fae as I can see... 
Please, do not think that I'm trying to compete, I'm just making a joke...

---

### Post by Penguin Guy on 2010-05-31
[@zika]("http://ubuntuforums.org/images/buttons/viewpost.gif")

I've attached my corrected version, but here's the relevant part:
```

                ;;
            *)
                COMPREPLY=( $( apt-cache --no-generate pkgnames "$cur" \
                    2> /dev/null )
                return 0
                ;;
        esac

```
I'd also be interested to see your unpatched version of the file.

EDIT: Oops, I think I might have posted the wrong file.

---

### Post by zika on 2010-05-31
> **Penguin Guy said:**
> [@zika]("http://ubuntuforums.org/images/buttons/viewpost.gif")

I've attached my corrected version, but here's the relevant part:
```

                ;;
            *)
                COMPREPLY=( $( apt-cache --no-generate pkgnames "$cur" \
                    2> /dev/null )
                return 0
                ;;
        esac

```
I'd also be interested to see your unpatched version of the file.I think this is the one, but I am not completely sure if this is not changed a bit from the "real" original...
The "main" discussion about this is in the "other" thread, given above in my message...

---

### Post by Penguin Guy on 2010-05-31
> **zika said:**
> I think this is the one, but I am not completely sure if this is not changed a bit from the "real" original...
The "main" discussion about this is in the "other" thread, given above in my message...
The patch I gave you should work for a fresh version of /etc/bash_completion.d/apt, if you've modified the file the patch may fail. I'll also post the patch in the main thread.

---

### Post by Penguin Guy on 2010-05-31
I've attached a patch that should fix the problem, just [download it]("http://ubuntuforums.org/attachment.php?attachmentid=158906&d=1275327707") and run this:
```
sudo patch /etc/bash_completion.d/apt **/path/to/**apt_completion.txt
```
*(it's a [FONT="Courier New"].txt[/FONT] to bypass the file filter)*


NOTE: The patch may fail if you have previously edited the file, get a fresh one by running:
```
sudo apt-get install --reinstall apt bash-completion
```

---

### Post by cariboo on 2010-05-31
Since the two bash completion threads were about the same thing, I merged them.

---

### Post by zika on 2010-05-31
> **cariboo907 said:**
> Since the two bash completion threads were about the same thing, I merged them.Thank You. (I was the one that asked for that...)

---

### Post by crjackson on 2010-05-31
> **zika said:**
> Thank You. (I was the one that asked for that...)

My apologies, I guess I stupidly caused the 2nd thread. I didn't know that "bash-completion" was the same error I was having. :(

---

### Post by cariboo on 2010-05-31
> **zika said:**
> Thank You. (I was the one that asked for that...)

I merged the thread before I saw your report. :)

---

### Post by Reiger on 2010-05-31
@Zika: I don't know why that is there, either: I simply modified the line which caused the error and left everything else intact.

@Penguin Guy: from what I saw in the code-block you posted, you've actually taken out a second entry (and a missing closing parenthesis), too: the bash completion thing seems to check for packages named "$cur" as well as "lib$cur" in the original file. This would suggest that there's some kind of auto-completion of package names going on where you might have autocompletion of qt4-webkit into libqt4-webkit. I'm not sure, though as I don't actually use the apt completion features of this package...

---

### Post by Penguin Guy on 2010-05-31
> **Reiger said:**
> @Penguin Guy: from what I saw in the code-block you posted, you've actually taken out a second entry (and a missing closing parenthesis), too: the bash completion thing seems to check for packages named "$cur" as well as "lib$cur" in the original file. This would suggest that there's some kind of auto-completion of package names going on where you might have autocompletion of qt4-webkit into libqt4-webkit. I'm not sure, though as I don't actually use the apt completion features of this package...
I don't know what happened there, but I somehow deleted the bracket (check the .diff - you'll see they're both there). As for the [FONT="Courier New"]lib$cur[/FONT] part - you're right about what it does. The [FONT="Courier New"]lib$cur[/FONT] part was added by [this patch]("http://launchpadlibrarian.net/41950277/546794.patch") which also caused the error. Being a minor feature, I figured the safest thing was to simply undo the patch until the developers can release a proper fix.

---

### Post by zika on 2010-05-31
> **Penguin Guy said:**
> I don't know what happened there, but I somehow deleted the bracket (check the .diff - you'll see they're both there). As for the [FONT="Courier New"]lib$cur[/FONT] part - you're right about what it does. The [FONT="Courier New"]lib$cur[/FONT] part was added by [this patch]("http://launchpadlibrarian.net/41950277/546794.patch") which also caused the error. Being a minor feature, I figured the safest thing was to simply undo the patch until the developers can release a proper fix.I've done the same... Look in the proposed file I've posted. I've done it because I concur with the argument given in aforementioned bug... I do nit want to have lib inserted in front of a string I give for TAB-completion... So, aside from simple syntax correction we (both of us) simply reverted to the previous state of bash_completion algorithm... Of course, by simple omitting ";" on proper places, You could preserve new, proposed behaviour... I beg to differ...
So, to conclude, the final product(s) we gave are the same, only the reasoning behind it is a bit different...

Update: As it can be seen:```
            *)
                COMPREPLY=( $( apt-cache --no-generate pkgnames "$cur" \
                    2> /dev/null ) )
                return 0
                ;;
        esac
```from the newest version of bash-completion, the dev-s've done the same...

---

### Post by zika on 2010-06-01
NOS version of bash_completion is out. This was a nice étude...

---

### Post by jppr on 2010-06-01
new bash is upgraded now

---

### Post by Penguin Guy on 2010-06-03
Since this issue is resolved it might be a good idea to mark this thread as solved, thanks.

P.S. Accidental rhyme :).

---

### Post by zika on 2010-06-03
> **Penguin Guy said:**
> Since this issue is resolved it might be a good idea to mark this thread as solved, thanks.

P.S. Accidental rhyme :).Rhyme or no rhyme, it was marked [solved] as soon it was solved... At least I do see it as marked...

---

### Post by Penguin Guy on 2010-06-03
> **zika said:**
> Rhyme or no rhyme, it was marked [solved] as soon it was solved... At least I do see it as marked...
Must have got it mixed up with another thread somehow, sorry.

---

### Post by cariboo on 2010-06-03
I marked it solved after a saw Penguin Guy's post. :)

---

### Post by zika on 2010-06-04
> **cariboo907 said:**
> I marked it solved after a saw Penguin Guy's post. :)
:-k:-\"=D>

---

### Post by Penguin Guy on 2010-06-04
> **cariboo907 said:**
> I marked it solved after a saw Penguin Guy's post. :)
I'm not crazy! :D

---

### Post by zika on 2010-06-04
> **Penguin Guy said:**
> I'm not crazy! :DMe too! :)

---

