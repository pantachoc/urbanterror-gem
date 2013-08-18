urbanterror-gem
===============

Provides a class and utilities to get informations and control Urban Terror servers via UDP queries.

## Installation

`gem install urbanterror`

## Examples
### Get player list and server's settings
  
	require 'urbanterror'
		
	sv = UrbanTerror::Server.new 'myserveraddressonthe.net' #You can omit port, It'll use the default port: 27960
	sv.update_status
		
	puts 'Player list'
	sv.players.each do |player|
       	puts "#{player[:name]} with #{player[:score]} points and #{player[:ping]}ms ping"
	end
		
	puts 'settings list'
	sv.settings.each do |cvar, value|
       	puts "#{cvar} = #{value}"
	end

### Do some rcon commands 

	require 'urbanterror'
		
	sv = UrbanTerror::Server.new 'myserveraddressonthe.net', 1337, 'myl33tRc0np4$$w0rd'
	puts sv.rcon 'status'

### Useful utilities inside ;)

	require 'urbanterror'
	
	gears = UrbanTerror::reverse_gear_calc 7
	# Returned value: ["knives", "pistols", "autos", "negev"]
	
	gear_code = UrbanTerror::gear_calc ['snipers', 'pistols']
	# Returned value: 53

	gt = UrbanTerror::gametype_name 8
	# Returned value "Capture the Flag"
	