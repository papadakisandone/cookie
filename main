from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import keyboard

chrome_driver_path = "c:\Development\chromedriver.exe"
driver = webdriver.Chrome(executable_path=chrome_driver_path)

# Getting current URL
# url = driver.current_url
upgrades_cost = {}
url = "https://orteil.dashnet.org/cookieclicker/"
driver.get(url)

cookie = driver.find_element_by_css_selector("#bigCookie")

bakery_name = driver.find_element_by_id("bakeryName")
bakery_name.click()
name_input = driver.find_element_by_id("bakeryNameInput")
name_input.send_keys("Antonis")
confirm = driver.find_element_by_id("promptOption0")
confirm.click()




def upgrade_items_cost_test():

    # fere ola ta div pou ksekinane me productName
    # products_names = driver.find_elements_by_css_selector("div[class=title][id^=productName]")
    # print(product_names)
    upgrades = driver.find_elements_by_css_selector("div[class=content]")
    for index_t, line in enumerate(upgrades):
        upgrade_name = line.find_element_by_css_selector("div #productName" + str(index_t)).text
        price = line.find_element_by_css_selector("#productPrice" + str(index_t)).text

        if len(upgrade_name) < 1:  # ean den einai visible, diathesimo
            upgrade_name = "???"
        if price == "":
            price = 0

        # print(price)

        # add to dictionary upgrade name and cost
        add_to_dict = {
            index_t: {upgrade_name: price}
        }
        upgrades_cost.update(add_to_dict)
    print(upgrades_cost)

    # my cookies currency
    cookie_count = driver.find_element_by_id("cookies").text  # posa cookies exo
    my_cookies = cookie_count.split(' ')[0]
    my_cookies_end = cookie_count.split(' ')[1].split('\n')[0]


    print(my_cookies, my_cookies_end)



def wait_loop():
    wait = True
    while wait:
        if keyboard.is_pressed("s"):  # start
            click_loop()
        if keyboard.is_pressed("u"):  # upgrade
            upgrade_items_cost_test()


def click_loop():
    game = True
    while game:
        cookie.click()
        # if keyboard.is_pressed("e"):  # exit
        #     game = False
        if keyboard.is_pressed("w"):  # wait
            wait_loop()


wait_loop()
