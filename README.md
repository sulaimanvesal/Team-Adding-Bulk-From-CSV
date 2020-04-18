# Team-Adding-Bulk-From-CSV

Adding Bulk members using a CSV file:
How to proceed:
    Open **Windows PowerShell** by running as **Administrator** 
    To see the modules: 
   
    'get-module | ft name, version' 
   
   To use Add-TeamChannelUser command, before installing **MicorsoftTeams (1.0.18)** package we need to add external package library as following:
    
      'Register-PSRepository –Name '_TempTestRepo' –SourceLocation 'https://www.poshtestgallery.com''
      'Get-PSRepository | Fl'
Now you can install the desired version of MicrosoftTeams  (Adding bulk users to channel works on 1.0.18v above)
      
      'Install-Module MicrosoftTeams –RequiredVersion 1.0.20'
To access the Teams, we need TeamID, how to get:
      
      'Get-Team -DisplayName "Deep Learning Exercises (SoSe20)"'
Everything is done, now we need to create a csv file:
        
        a.	Column name should be: email
        b.	Each row should have the following email address: ec09ypaf@fauad.fau.de
        c.	Save it as test.csv
To add the members to channel e.g. TestChan we need to run the following command:

    'Import-Csv -Path "test.csv" | foreach{Add-TeamChannelUser -GroupId b6bb4238-b333-4b30-97c2-376a35b96220 -DisplayName "TestChan" -user $_.email}'
Done. Now the users should be a member of TestChan
