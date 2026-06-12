---
title: "Configure conkyrc"
date: 2022-09-03
forum: Multimedia Software
---

### Post by affarone2 on 2022-09-03
Ciao a tutti.
Sul mio file conkyrc ho impostato questo codice come segue.
Su Linux Mint va tutto bene la trasparenza è ottima ma su Lubuntu lo sfondo rimane nero. hai una soluzione?




```
[# Lubuntu-CONKY# Uno script conky completo, configurato per l'uso su# Ubuntu / Debian Gnome, senza bisogno di script esterni.## Basato su conky-jc e .conkyrc predefinito.# INCLUDE:# - coda di /var/log/messages # - connessioni netstat al tuo computer## #
# Crea la tua finestra invece di usare il desktop (richiesto in nautilus)propria_finestra siown_window_hints non decorato,sotto,skip_taskbarsfondo n
# Usa il doppio buffering (riduce lo sfarfallio, potrebbe non funzionare per tutti)double_buffer sì
# giocherellare con la finestrause_spacer siuse_xft sì
# Intervallo di aggiornamento in secondiaggiornamento_intervallo 3.0
# Dimensione minima dell'area di testodimensione_minima 400 5
# Disegna le sfumature?draw_shades si
# Roba di testodraw_outline no # amplifica il testo se sìdraw_borders n
maiuscolo no # impostato su yes se si desidera che tutto il testo sia in maiuscolo
# Bordi punteggiati?stippled_borders 8
# margini di confinemargine_bordo 4
# larghezza del bordolarghezza_bordo 1
# Colori predefiniti e anche colori dei bordi, grey90 == #e5e5e5default_colore biancodefault_shade_color nerodefault_outline_color bianco
# Colore Finestra propria_finestra_colore marroneown_window_transparent sì
# Allineamento del testo, vengono commentati altri possibili valori#allineamento in alto a sinistraallineamento in alto a destra#allineamento in basso_sinistra#allineamento in basso_destra
# Spazio tra i bordi dello schermo e il testogap_x 10gap_y 10
# gli elementi dopo "TESTO" verranno formattati sullo schermo
override_utf8_locale noxftfont Terminus: size=8xftalfa 0,8
TESTO
${offset 240}${colore grigio ardesia}${ora %a, } ${colore }${ora %e %B %G}${offset 240}${colore grigio ardesia}${ora %Z, }${colore }${ora %H:%M:%S}${offset 240}${colore grigio ardesia}Tempo di attività: ${colore }$tempo di attività${offset 240}${colore grigio ardesia}Kern:${color }$kernel${offset 240}${colore grigio ardesia}CPU:${colore } $cpu% ${acpitemp}C${offset 240}${cpugraph 20,130 000000 ffffff}${offset 240}${colore grigio ardesia}Carico: ${colore }$loadavg${offset 240}${colore grigio ardesia}Processi: ${colore }$processi  ${offset 240}${color slate grey}In esecuzione: ${color }$running_processes
${offset 240}${color slate grey}CPU più alta:${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}${offset 240}${colore grigio chiaro} ${top name 2}${top cpu 2}${offset 240}${colore grigio chiaro} ${top name 3}${top cpu 3}${offset 240}${colore grigio chiaro} ${top name 4}${top cpu 4}
${offset 240}${color slate grey}MEM più alta:${offset 240}${colore #ddaa00} ${top_mem nome 1}${top_mem mem 1}${offset 240}${colore grigio chiaro} ${top_mem nome 2}${top_mem mem 2}${offset 240}${colore grigio chiaro} ${top_mem nome 3}${top_mem mem 3}${offset 240}${colore grigio chiaro} ${top_mem nome 4}${top_mem mem 4}
${offset 240}${colore grigio ardesia}MEM: ${colore } $memperc% $mem/$memmax${offset 240}${membar 3,100}${offset 240}${colore grigio ardesia}SWAP: ${colore }$swapperc% $swap/$swapmax${offset 240}${barra di scambio 3.100}
${offset 240}${colore grigio ardesia}ROOT: ${colore }${fs_free /}/${fs_size /}${offset 240}${fs_bar 3.100 /}${offset 240}${colore grigio ardesia}HOME: ${colore }${fs_free /home}/${fs_size /home}${offset 240}${fs_bar 3.100 /home}${offset 240}${colore grigio ardesia}SLACK: ${colore }${fs_free /mnt/slack}/${fs_size /mnt/slack}${offset 240}${fs_bar 3.100 /mnt/slack}${offset 240}${colore grigio ardesia}NET: ${offset 240}${color}Su: ${color }${upspeed eth0} k/s${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}${offset 240}${color}Giù: ${color }${downspeed eth0}k/s${color}${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}
```

---

