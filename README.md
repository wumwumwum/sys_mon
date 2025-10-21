# sys_mon
System Health &amp; Resource Monitor (Python)

Sample Project #1

The goal was to create a sciprt that would log system health information but could also alert is there is an issue. 

Steps:
1. I ensured that Python 3 was installed (it was) and verified the version (python 3.13)
2. I opened a cmd (admin) and installed psutil using:

		pip install psutil

3. I created a .py file by opening Notepad++ and creating a file called sys_mon.py and saved the file. 
4. I verified that the file was created and was a py file
5. I opened the sys_mon.py file in Notepad++ and wrote the following:

		import psutil, time, csv, datetime

		with open("system_log.csv", "a", newline="") as f:
  			writer = csv.writer(f)
  			writer.writerow(["Timestamp", "CPU%", "RAM%", "Disk%"])

    	while True:
        	cpu = psutil.cpu_percent()
        	ram = psutil.virtual_memory().percent
        	disk = psutil.disk_usage('/').percent
        	now = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        	writer.writerow([now, cpu, ram, disk])
        	f.flush()
        	time.sleep(60)

6. Testing. Ran py file test functionality. In cmd,:

		python sys_mon.py

7. Opened file "system_log.csv" located in same directory as py script
