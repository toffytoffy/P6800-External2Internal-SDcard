P6800-External2Internal-SDcard
==============================

สำหรับ galaxy tab7.7 และรุ่นอื่นๆ ก็สามารถใช้ได้นะครับ มีอยู่2วิธี 1.วิธีแรก ใช้แอพเอาครับ แต่ต้องรูทเครื่องก่อน ให้ไปโหลด แอพ Root external2internal ในเพลย์สโตร์มานะครับ วิธีนี้เวลารีบูทจะกลับเป็นเหมือนเดิม อาจจะมีปัญหากับแอพไหม่ๆที่ติดตั้ง 2.ส่วนวิธีที2ของผมคือเขียนสคริปเอาครับ -ก่อนอื่นให้ไปโหลด Smanager มาลงไว้ -่ไปที่/system/etc/init.d/ -แล้วสร้างสคริป #!/system/bin/sh #extsd2internalsd is a modification that allows to switch internal sd to external sd and viceversa. With this you can use default internal sd only for app storage #and the external sd to store all apps resource and all others stuff. The resut is a very big increase of installable apps on GalaxyTab7.7 #All credits to Snowxucker of xda forum for the idea and script and to GalaxyTAB7.7 for the cmw zip.  #xda thread url at sleep 10 mount -o remount,rw / mount -t vfat -o umask=0000 /dev/block/vold/179:24 /mnt/sdcard mount -t vfat -o umask=0000 /dev/block/vold/179:25 /storage/sdcard0 sleep 30 mount -o bind /data/media /mnt/emmc mount -o bind /data/media /storage/sdcard chmod 777 /mnt/emmc sleep 30 mkdir -p /mnt/emmc /external_sd/sdcard1 touch /mnt/extSdCard/external_sd/ sleep 10 mount -o bind /storage/sdcard0 /mnt/emmc/storage/sdcard1 exit หรือ #!/system/bin/sh sleep 50 mount -o remount,rw / mkdir -p /data/internal_sd mount -o bind /mnt/sdcard /data/internal_sd mount -t null -o umask=0000 /dev/block/vold/179:24 /mnt/sdcard chmod 777 /data/internal_sd mkdir -p /storage/HDD  mount -o bind /data/media /mnt/sdcard mount -t exfat -o umask=0000 /dev/block/vold/179:26 /mnt/sdcard/extsd2 mount -o bind /mnt/sdcard/extsd2 /storage/sdcard0 chmod 777 /data/extsd2 /storage/sdcard1 exit อันแรกจะมองไม่เห็น sdcardภายในนะครับ อันที่2จะมองเห็น sdcardที่ย้ายไปในตัวเครื่อง -จากนั้นก็ Run สคริป ติ้ก su และ run onboot เพื่อที่ไม่ให้สลับกลับเวลารีบูทครับ -จากนั้นก็รันสคริป ครับ  รอประมาน10วินาทีก็จะเห็นว่าเมมภายนอกสลับกับเมมภายในแล้ว  -ให้ไปเช็คดูที่settingครับ เครดิตจาก xdaนะครับ ผมไปเอาสคริป ที่เขาเขียนไว้มาต่อยอด EXT4 คืออะไร http://ext48nvvtwi.blogspot.com/ ext2intsd        